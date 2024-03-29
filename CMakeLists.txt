cmake_minimum_required(VERSION 3.26)
project(Geant4)

set(CMAKE_CXX_STANDARD 17)

add_executable(Geant4 main.cpp
        XRF.cpp
        XRF.cpp
        construction.cc
        construction.hh)
find_package(Geant4 REQUIRED ui_all vis_all)

include(${Geant4_USE_FILE})

file(GLOB sources ${PROJECT_SOURCE_DIR}/*.cc)
file(GLOB headers ${PROJECT_SOURCE_DIR}/*.hh)

add_executable(XRF XRF.cpp ${sources} ${headers}
        construction.cc
        construction.hh)
target_link_libraries(XRF ${Geant4_LIBRARIES})

add_custom_target(Geant4 DEPENDS XRF)
