cmake_minimum_required(VERSION 3.5)

find_package(ros_industrial_cmake_boilerplate REQUIRED)
extract_package_metadata(pkg)
project(${pkg_extracted_name} VERSION ${pkg_extracted_version} LANGUAGES CXX)

configure_package()

install(DIRECTORY launch urdf meshes rviz DESTINATION share/${PROJECT_NAME}/)

