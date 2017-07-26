cmake_minimum_required(VERSION 2.8.11)

project(icub-gazebo-wholebody)

# Add models
add_subdirectory(models)

# Add worlds
add_subdirectory(worlds)

# Install the files
install(DIRECTORY ${CMAKE_BINARY_DIR}/gazebo DESTINATION share)
