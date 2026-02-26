cmake_minimum_required(VERSION 3.0.2)
project(grasping_pipeline_msgs)

find_package(catkin REQUIRED
  genmsg 
  actionlib
  actionlib_msgs
  geometry_msgs
  std_msgs
  vision_msgs
  object_detector_msgs
)

## Generate messages in the 'msg' folder
add_message_files(
  FILES
  BoundingBox3DStamped.msg
  GraspInput.msg
  GraspOutput.msg
  Plane.msg
)

## Generate services in the 'srv' folder
add_service_files(
  FILES
  CallDirectGraspPoseEstimator.srv
  CallMultipleDirectGraspPoseEstimator.srv
  CallObjectDetector.srv
  CallPoseEstimator.srv
  FetchImages.srv
  FindTablePlanes.srv
  GetBBOfObjectsOnTable.srv
  GetPCOfObjectsOnTable.srv
  GoBack.srv
  GoToWaypoint.srv
  GraspApproachVector.srv
  GraspCalculationTimeMax.srv
  GraspMethodSelector.srv
  GraspPreGripperOpeningWidth.srv
  GraspSearchCenter.srv
  GraspSearchRectangleSize.srv
  MoveToJointPositions.srv
  RemoveNonTableObjects.srv
  SetCollisionEnvironment.srv
  ShowOnlyBestGrasp.srv
  TablePlaneExtractor.srv
  TextToSpeech.srv
  VisualizePoseEstimation.srv
)

# Generate actions in the 'action' folder
add_action_files(
  FILES
  CalcGraspPointsServer.action
  ExecuteGrasp.action
  FindGrasppoint.action
  FindMultipleGrasppoint.action
  Handover.action
  Place.action
)

# Generate added messages and services with any dependencies listed here
generate_messages(
  DEPENDENCIES
  actionlib_msgs
  geometry_msgs
  std_msgs 
  vision_msgs
  object_detector_msgs
)

catkin_package()

include_directories()