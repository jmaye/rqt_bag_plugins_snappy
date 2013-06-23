cmake_minimum_required(VERSION 2.6)

include(ReMake)

remake_project(
  rqt-bag-plugins-snappy-${ROS_DISTRIBUTION}
  VERSION 0.1
  RELEASE alpha
  SUMMARY "RQT plugins for snappy messages."
  AUTHOR "Jerome Maye"
  CONTACT "jerome.maye@mavt.ethz.ch"
  HOME "http://github.com/jmaye/rqt_bag_plugins_snappy"
  LICENSE "GNU Lesser General Public License (LGPL)"
  PREFIX rqt-bag-plugins-snappy-
  INSTALL /usr
  CONFIGURATION_DESTINATION /etc/rqt-bag-plugins-snappy
  EXTRA_CXX_FLAGS -std=c++0x
)

remake_var_name(GIT_REVISION_VAR ${REMAKE_PROJECT_NAME} GIT_REVISION)

remake_ros_pack_deb()

if(${ROS_DISTRIBUTION} STREQUAL fuerte)
  remake_ros_distribute_deb(
    DISTRIBUTION lucid
    SECTION libs
    DEPENDS remake pkg-config
    UPLOAD ppa:jmaye/ros
    PASS CMAKE_BUILD_TYPE ${GIT_REVISION_VAR}
    FORCE_CONSISTENCY
  )
endif()

remake_ros_distribute_deb(
  DISTRIBUTION precise
  SECTION libs
  DEPENDS remake pkg-config
  UPLOAD ppa:jmaye/ros
  PASS CMAKE_BUILD_TYPE ${GIT_REVISION_VAR}
  FORCE_CONSISTENCY
)
