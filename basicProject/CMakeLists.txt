if(NOT DEFINED CMGym_DIR)
   set(CMGym_DIR "${CMAKE_CURRENT_LIST_DIR}/../../" CACHE STRING "The top directory of CMGym")
endif()

include(${CMGym_DIR}/scripts/core.cmake)
add_subdirectory("${CMAKE_CURRENT_LIST_DIR}/libs/staticLib")
add_subdirectory("${CMAKE_CURRENT_LIST_DIR}/libs/dynamicLib")

startProj(BasicProject)

addIncludesAuto(${CMAKE_CURRENT_LIST_DIR}/src CMFT_SRC_c++ Source/sourcefilesdummy)
addIncludesAuto(${CMAKE_CURRENT_LIST_DIR}/include CMFT_HEADER_c++ Headers/headerfilesdummy)

add_executable(bean "${INCLUDES}")
bindIncludes(bean)
setMain(bean)

target_link_libraries(bean SLIB)

endProj(BasicProject)