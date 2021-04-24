# ------------------------------------------------------------------------------

# // - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
#
# @about
# Asteroids2D - 2D top-down arcade shooter.
#
# License: see "LICENSE" file.
#
# @min.requirements
# - C++ 11 with exceptions support;
#
# @output
# - STATIC Library || Executable;
#
# @tests
# - none;
#
# // - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

# =================================================================================
# CMake Meta-Data
# =================================================================================

# CMake-Version
cmake_minimum_required ( VERSION 3.6 FATAL_ERROR ) # QT & Android

# =================================================================================
# CONSTANTS
# =================================================================================

set( CMAKE_INCLUDES_DIR "src/zeroSDK/cmake/" )
set( CMAKE_GAME_INCLUDES_DIR "cmake/" )

set( ASTEROIDS_SRC_DIR "src/asteroids2d" )
set( ASTEROIDS_PUBLIC_DIR "${ASTEROIDS_SRC_DIR}/public/" )
set( ASTEROIDS_PRIVATE_DIR "${ASTEROIDS_SRC_DIR}/private/" )

# =================================================================================
# CONFIGS
# =================================================================================

# Platform
include( "${CMAKE_INCLUDES_DIR}platform.cmake" )

# =================================================================================
# OPTIONS
# =================================================================================

set ( CXX_VERSION 11 )

# =================================================================================
# PROJECT
# =================================================================================

# Project Name
set ( PROJECT_NAME "Asteroids2D" )

# Project Version
set ( PROJECT_VERSION 0.0.1 )

# Project Description
set ( PROJECT_DESCRIPTION "Asteroids2D" )

# Configure Project
project ( ${PROJECT_NAME} VERSION ${PROJECT_VERSION} DESCRIPTION ${PROJECT_DESCRIPTION} LANGUAGES C CXX )

# C++ Version
set ( CMAKE_CXX_STANDARD ${CXX_VERSION} )
#set ( CMAKE_CXX_STANDARD 17 ) # Android stdlibc++ 14+
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_INCLUDE_CURRENT_DIR ON)

set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)

# Set Flags
# Flags:
# -fexceptions - enable C++ exceptions (GCC & MSVC), fcxx-exceptions (Clang);
set ( CMAKE_CXX_FLAGS "-fexceptions -fcxx-exceptions" ${CMAKE_CXX_FLAGS} )

# =================================================================================
# GAME
# =================================================================================

# Core
add_subdirectory ( "${ASTEROIDS_SRC_DIR}/core" )

# Platform.Executable
if ( WINDOWS )
    add_subdirectory ( "${ASTEROIDS_SRC_DIR}/windows" )
else ( WINDOWS )
    message ( FATAL_ERROR "${PROJECT_NAME} - unsupported platform for executable" )
endif ( WINDOWS )

# =================================================================================
# ENGINE
# =================================================================================

# zeroSDK
set ( ZERO_SRC_DIR "src/zeroSDK" )
add_subdirectory ( ${ZERO_SRC_DIR} )

# ------------------------------------------------------------------------------
