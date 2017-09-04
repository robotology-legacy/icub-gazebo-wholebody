# configure_files for all files in a folder
# https://stackoverflow.com/questions/697560/how-to-copy-directory-from-source-tree-to-binary-tree
macro(CONFIGURE_FILES srcDir destDir)
  make_directory(${destDir})
  file(GLOB_RECURSE templateFiles RELATIVE ${srcDir} ${srcDir}/*)

  foreach(templateFile ${templateFiles})
    set(srcTemplatePath ${srcDir}/${templateFile})
    message(${srcTemplatePath})

    if(NOT IS_DIRECTORY ${srcTemplatePath})
      configure_file(${srcTemplatePath}
                     ${destDir}/${templateFile}
                     @ONLY)
    endif()

  endforeach(templateFile)

endmacro(CONFIGURE_FILES)

# Allow specifying the robot name (default to "icub" for backwards compatibility)
set(ROBOT_NAME "icub" CACHE STRING "Select the the robot name that will also match the sdf's model://{ROBOT_NAME} (model folder searched by Gazebo)")

# Setup the build tree
CONFIGURE_FILES(${CMAKE_SOURCE_DIR}/models ${CMAKE_BINARY_DIR}/gazebo/)
