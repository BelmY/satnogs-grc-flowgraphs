#
#  satnogs-flowgraphs: SatNOGS GNU Radio flowgraphs
#
#  Copyright (C) 2020
#  Libre Space Foundation <http://libre.space>
#
#  This program is free software: you can redistribute it and/or modify
#  it under the terms of the GNU General Public License as published by
#  the Free Software Foundation, either version 3 of the License, or
#  (at your option) any later version.
#
#  This program is distributed in the hope that it will be useful,
#  but WITHOUT ANY WARRANTY; without even the implied warranty of
#  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#  GNU General Public License for more details.
#
#  You should have received a copy of the GNU General Public License
#  along with this program.  If not, see <http://www.gnu.org/licenses/>
#

cmake_minimum_required(VERSION 3.8)
project(satnogs-flowgraphs )

########################################################################
# Find build dependencies
########################################################################
find_package(PythonLibs 3)
find_package(Gnuradio "3.8" REQUIRED 
             COMPONENTS runtime blocks fft analog filter digital pmt)
include(GrVersion)

# gr-soapy and gr-satnogs are also required for the compilation
find_package(soapy REQUIRED)
find_package(satnogs REQUIRED)

########################################################################
# Create uninstall target
########################################################################
configure_file(
    ${CMAKE_SOURCE_DIR}/cmake/cmake_uninstall.cmake.in
    ${CMAKE_CURRENT_BINARY_DIR}/cmake_uninstall.cmake
@ONLY)

add_custom_target(uninstall
    ${CMAKE_COMMAND} -P ${CMAKE_CURRENT_BINARY_DIR}/cmake_uninstall.cmake
)


add_subdirectory(generic)
add_subdirectory(satellites)