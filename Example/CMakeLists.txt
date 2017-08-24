#=============================================================================
# (c) Kiyoyuki Chinzei, AIST japan.
# Small Computings for Clinicals
# Do not remove this copyright claim and the license conditions below.
# This file is released under two licenses: the BSD 3-Clause license and the MIT license.
# See https://opensource.org/licenses
# You may pick the license that best suits your needs.
#=============================================================================

CMAKE_MINIMUM_REQUIRED(VERSION 2.8)

# Modify for your app
SET(app myapp)
SET(src_files main.cpp)
SET(inc_files)

PROJECT(${app})

# To find FindDeckLinkSDK.cmake in the source directory.
# You specify the path where you put FindDeckLinkSDK.cmake.
SET(CMAKE_MODULE_PATH ${CMAKE_SOURCE_DIR})

FIND_PACKAGE(DeckLinkSDK 10.0 REQUIRED)

IF(DeckLinkSDK_FOUND)
  INCLUDE_DIRECTORIES("${DeckLinkSDK_INCLUDE_PATH}")
  IF   (COMPILE_DEFINITIONS)
    SET(COMPILE_DEFINITIONS "${COMPILE_DEFINITIONS};${DeckLinkSDK_DEF}")
  ELSE (COMPILE_DEFINITIONS)
    SET(COMPILE_DEFINITIONS ${DeckLinkSDK_DEF})
  ENDIF(COMPILE_DEFINITIONS)
  ADD_EXECUTABLE(${app} ${src_files} ${inc_files} "${DeckLinkSDK_SRC_FILE}")
  TARGET_LINK_LIBRARIES(${app} ${DeckLinkSDK_LIBS})
ENDIF(DeckLinkSDK_FOUND)


