# Get all cpp files in current directory.
file(GLOB apps_list RELATIVE ${CMAKE_CURRENT_SOURCE_DIR} *.cpp)

foreach(app_filename ${apps_list})
  # Get file name without extension.
  get_filename_component(app ${app_filename} NAME_WE)
  # Add and configure executable file to be produced .
  add_executable(${app} ${app_filename})
  target_link_libraries(${app} ${LIBRARY_DEPS})
  set_target_properties(${app} PROPERTIES
    OUTPUT_NAME "${app}"
    PROJECT_LABEL "${app}"
    RUNTIME_OUTPUT_DIRECTORY "../")
endforeach()
