cmake_minimum_required(VERSION 3.16)

project(Chap02)

find_package(VTK REQUIRED)
if (NOT VTK_FOUND)
  message("Skipping example: ${VTK_NOT_FOUND_MESSAGE}")
  return ()
endif ()

foreach(TARGET_NAME 2.1_render_cylinder 2.2_render_cylinder-lights 2.2_render-cylinder-camera
             2.2_texture_example 2.3_viewport 2.4_pipeline_execute 2.4_vtk_pipeline_demo 
             2.5_reference_counting)
  set(SRCS ${TARGET_NAME}.cpp)
  add_executable(${TARGET_NAME} ${SRCS})
  vtk_module_autoinit(
    TARGETS ${TARGET_NAME}
    MODULES ${VTK_LIBRARIES})
endforeach()
