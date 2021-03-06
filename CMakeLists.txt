cmake_minimum_required (VERSION 3.13)

project (Geotec)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

include(cmake/StandardProjectSettings.cmake)

# Enables NeoPZ library
include(cmake/EnableNeoPZ.cmake)
enable_pz()

# Enables log4cxx library
include(cmake/EnableLog4CXX.cmake)
enable_log4cxx()

# This option enables a lot of warnings and treat them as errors, to ensure
# good programming practices are used. Since its behaviour is extreme, it
# should be turned off by default.
option(ENABLE_ALL_WARNINGS "Enable a lot of compiler warnings and treat them as errors" OFF)
if (ENABLE_ALL_WARNINGS)
    add_library(project_warnings INTERFACE)
    include(cmake/CompilerWarnings.cmake)
    set_project_warnings(project_warnings)
    set(CMAKE_CXX_FLAGS "")
endif()

add_subdirectory(FiniteDiff)

