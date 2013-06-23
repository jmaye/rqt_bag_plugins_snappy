remake_ros_package(
  rqt_bag_plugins_snappy
  DEPENDS rospy roslib rqt_bag sensor_msgs mv_cameras
  DESCRIPTION "RQT plugins for snappy messages."
  EXTRA_RUN_DEPENDS libsnappy-python
)
