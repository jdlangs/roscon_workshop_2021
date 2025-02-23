cmake_minimum_required(VERSION 3.5)
project(snp_application)

# Default to C99
if(NOT CMAKE_C_STANDARD)
  set(CMAKE_C_STANDARD 99)
endif()

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)

if(CMAKE_VERSION VERSION_LESS "3.7.0")
    set(CMAKE_INCLUDE_CURRENT_DIR ON)
endif()

find_package(Qt5 COMPONENTS Widgets REQUIRED)

find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(snp_msgs REQUIRED)

include_directories(include)

add_executable(roscon_app
    src/rosconwindow.ui
    src/rosconwindow.cpp
    src/main.cpp
    include/rosconwindow.h
)
target_link_libraries(roscon_app Qt5::Widgets)
ament_target_dependencies(roscon_app rclcpp snp_msgs)

install(TARGETS roscon_app DESTINATION lib/${PROJECT_NAME}/)

ament_package()