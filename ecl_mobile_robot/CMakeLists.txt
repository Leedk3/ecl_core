##############################################################################
# Cmake
##############################################################################

cmake_minimum_required(VERSION 3.5)
project(ecl_mobile_robot)

##############################################################################
# Find Packages
##############################################################################

# Turn -isystem off. Actually like to see warnings from underlying packages
# and regardless, have run into trouble because of the ordering it induces.
set(CMAKE_NO_SYSTEM_FROM_IMPORTED TRUE)

find_package(ament_cmake_ros REQUIRED)
find_package(ecl_build REQUIRED)
find_package(ecl_errors REQUIRED)
find_package(ecl_formatters REQUIRED)
find_package(ecl_geometry REQUIRED)
find_package(ecl_linear_algebra REQUIRED)
find_package(ecl_math REQUIRED)

##############################################################################
# Project Configuration
##############################################################################

ament_package_xml()
ecl_enable_cxx14_compiler()
ecl_enable_cxx_warnings()

##############################################################################
# Sources
##############################################################################

add_subdirectory(include)
add_subdirectory(src)

##############################################################################
# Exports
##############################################################################

ament_export_interfaces(HAS_LIBRARY_TARGET ${PROJECT_NAME})
ament_export_dependencies(
    ecl_errors
    ecl_formatters
    ecl_geometry
    ecl_linear_algebra
    ecl_math
)
ament_package()



