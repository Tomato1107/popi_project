#-------------------------------------------------------------------------------
#
# CMake file for the generated C++ code for the robot popi
#
# Author: Marco Frigerio
# Note: this file has been generated by RobCoGen.
#       Do not edit unless you know what you are doing.
#-------------------------------------------------------------------------------

# Project configuration
cmake_minimum_required(VERSION 2.8)
project(gen_popi)

set(EIGEN_ROOT   $ENV{EIGEN_ROOT}   CACHE PATH "Path to Eigen headers")
set(HEADER_INSTALL_ROOT /usr/local/include/ CACHE PATH "Where to install popi headers")
set(LIB_INSTALL_ROOT    /usr/local/lib/     CACHE PATH "Where to install popi library")

SET(CMAKE_CXX_FLAGS "-g -std=c++11 -Wall -O3 -D EIGEN_NO_DEBUG")

set(LIB_NAME iitgenpopi)

set(HEADERS ./declarations.h
            ./model_constants.h
            ./link_data_map.h
            ./joint_data_map.h
            ./transforms.h
            ./kinematics_parameters.h
            ./jacobians.h
            ./traits.h
            ./jsim.h
            ./inverse_dynamics.h
            ./forward_dynamics.h
            ./inertia_properties.h
            ./dynamics_parameters.h
            ./miscellaneous.h
            ./rbd_types.h
)
set(SOURCES ./transforms.cpp
            ./jacobians.cpp
            ./jsim.cpp
            ./inverse_dynamics.cpp
            ./forward_dynamics.cpp
            ./inertia_properties.cpp
            ./miscellaneous.cpp)

# Include directories
include_directories(${EIGEN_ROOT})

# Add library
add_library(${LIB_NAME} SHARED ${SOURCES})

# Install (ie copy) header files
install(FILES ${HEADERS} DESTINATION ${HEADER_INSTALL_ROOT}/iit/robots/popi/)

# Install the shared library
install(TARGETS ${LIB_NAME} LIBRARY DESTINATION ${LIB_INSTALL_ROOT})
