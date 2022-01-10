##  BSD 3-Clause License
##  
##  Copyright (c) 2022, Santhosh K
##  All rights reserved.
##  
##  Redistribution and use in source and binary forms, with or without
##  modification, are permitted provided that the following conditions are met:
##  
##  1. Redistributions of source code must retain the above copyright notice, this
##     list of conditions and the following disclaimer.
##  
##  2. Redistributions in binary form must reproduce the above copyright notice,
##     this list of conditions and the following disclaimer in the documentation
##     and/or other materials provided with the distribution.
##  
##  3. Neither the name of the copyright holder nor the names of its
##     contributors may be used to endorse or promote products derived from
##     this software without specific prior written permission.
##  
##  THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS"
##  AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
##  IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
##  DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE
##  FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL
##  DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR
##  SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER
##  CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY,
##  OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
##  OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

cmake_minimum_required(VERSION 3.0.0 FATAL_ERROR)

##  Cardinal version configuration
if(NOT DEFINED CARDINAL_PACKAGE_VERSION)
    set(CARDINAL_VERSION_MAJOR  0)
    set(CARDINAL_VERSION_MINOR  1)
    set(CARDINAL_VERSION_PATCH  0)
    set(CARDINAL_PACKAGE_VERSION ${CARDINAL_VERSION_MAJOR}.${CARDINAL_VERSION_MINOR}.${CARDINAL_VERSION_PATCH})
endif()

##  Cardinal CMake project configuration
if(CMAKE_SOURCE_DIR STREQUAL CMAKE_CURRENT_SOURCE_DIR)
    set(CARDINAL_STANDALONE_BUILD ON)
    project(Cardinal VERSION ${CARDINAL_PACKAGE_VERSION} LANGUAGES C)
endif()

##  Cardinal build - dicourage in-source builds
if(CMAKE_CURRENT_SOURCE_DIR STREQUAL CMAKE_CURRENT_BINARY_DIR)
    message(FATAL
    "In-source builds are strongly discouraged by the Cardinal project as it tends to pollute the source directory.
    Please create a dedicated source directory such as `build` or `build-cardinal` to store the build and configuration files.
    This process should have created `CMakeCache` folder and `CMakeFiles.txt` file in the source directory. Please delete these
    files before proceeding further.
    ")
endif()

##  Cardinal build - configurable options
option(CARDINAL_BUILD_STATIC        "Build static libraries for the Cardinal target"    ON)
option(CARDINAL_BUILD_SHARED        "Build shared libraries for the Cardinal target"    OFF)
option(CARDINAL_BUILD_DOCUMENTATION "Build documentation for the Cardinal target" ${CARDINAL_STANDALONE_BUILD})
option(CARDINAL_BUILD_EXAMPLES      "Build examples for the Cardinal target" ${CARDINAL_STANDALONE_BUILD})
option(CARDINAL_BUILD_UNIT_TESTS    "Build unit tests for the Cardinal target" ${CARDINAL_STANDALONE_BUILD})

##  Cardinal build - building library options
option(CARDINAL_BUILD_CARDINALDB    "Build the database engine of the Cardinal library" ON)

##  Cardinal build - Utility variable declaration
set(CARDINAL_ROOT_DIR ${CMAKE_CURRENT_SOURCE_DIR})
set(CARDINAL_INCLUDE_DIR ${CARDINAL_ROOT_DIR}/include)
set(CARDINAL_SOURCE_DIR ${CARDINAL_ROOT_DIR}/source)

##  Cardinal build - configure the `cardinal/configuration.h.in` file
configure_file(${CARDINAL_INCLUDE_DIR}/cardinal/configuration.h.in ${CARDINAL_INCLUDE_DIR}/cardinal/configuration.h)