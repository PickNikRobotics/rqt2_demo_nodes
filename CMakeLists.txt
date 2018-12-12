cmake_minimum_required(VERSION 3.5)
project(rqt2_demo_nodes)

find_package(ament_cmake REQUIRED)
find_package(ament_cmake_python REQUIRED)
find_package(rqt_py_common REQUIRED)
find_package(rosidl_default_generators REQUIRED)

set(rosidl_files
  "srv/Sum.srv"
  "msg/Val.msg"
  "msg/ArrayVal.msg"
)

rosidl_generate_interfaces(${PROJECT_NAME}
  ${rosidl_files}
  DEPENDENCIES
)

ament_python_install_package(${PROJECT_NAME}
  PACKAGE_DIR src/${PROJECT_NAME})

install(PROGRAMS scripts/example_service
  DESTINATION lib/${PROJECT_NAME}
)

ament_export_dependencies(rqt_py_common)
ament_export_dependencies(rosidl_default_runtime)

ament_package()
