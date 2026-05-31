cmake_minimum_required(VERSION 3.8)
project(grasping_pipeline_msgs)

# Required for ROS 2
find_package(ament_cmake REQUIRED)
find_package(rosidl_default_generators REQUIRED)

# Message / action dependencies
find_package(geometry_msgs REQUIRED)
find_package(std_msgs REQUIRED)
find_package(sensor_msgs REQUIRED)
find_package(vision_msgs REQUIRED)
find_package(builtin_interfaces REQUIRED)
find_package(action_msgs REQUIRED)

# If this package depends on messages from here
find_package(object_detector_msgs REQUIRED)

# Message files
set(msg_files
  "msg/BoundingBox3DStamped.msg"
  "msg/GraspInput.msg"
  "msg/GraspOutput.msg"
  "msg/Plane.msg"
)

# Service files
set(srv_files
  "srv/CallDirectGraspPoseEstimator.srv"
  "srv/CallMultipleDirectGraspPoseEstimator.srv"
  "srv/CallObjectDetector.srv"
  "srv/CallPoseEstimator.srv"
  "srv/FetchImages.srv"
  "srv/FindTablePlanes.srv"
  "srv/GetBBOfObjectsOnTable.srv"
  "srv/GetPCOfObjectsOnTable.srv"
  "srv/GoBack.srv"
  "srv/GoToWaypoint.srv"
  "srv/GraspApproachVector.srv"
  "srv/GraspCalculationTimeMax.srv"
  "srv/GraspMethodSelector.srv"
  "srv/GraspPreGripperOpeningWidth.srv"
  "srv/GraspSearchCenter.srv"
  "srv/GraspSearchRectangleSize.srv"
  "srv/MoveToJointPositions.srv"
  "srv/RemoveNonTableObjects.srv"
  "srv/SetCollisionEnvironment.srv"
  "srv/ShowOnlyBestGrasp.srv"
  "srv/TablePlaneExtractor.srv"
  "srv/TextToSpeech.srv"
  "srv/VisualizePoseEstimation.srv"
)

# Action files
set(action_files
  "action/CalcGraspPointsServer.action"
  "action/ExecuteGrasp.action"
  "action/FindGrasppoint.action"
  "action/FindMultipleGrasppoint.action"
  "action/Handover.action"
  "action/Place.action"
)

# Generate interfaces
rosidl_generate_interfaces(${PROJECT_NAME}
  ${msg_files}
  ${srv_files}
  ${action_files}
  DEPENDENCIES
    geometry_msgs
    std_msgs
    sensor_msgs
    vision_msgs
    builtin_interfaces
    action_msgs
)

# Export runtime dependencies
ament_export_dependencies(rosidl_default_runtime)
ament_export_include_directories(include)

ament_package()
