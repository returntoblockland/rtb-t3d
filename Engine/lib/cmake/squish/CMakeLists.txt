# Copyright (c) The rtb-t3d Contributors <https://github.com/returntoblockland/rtb-t3d>
#
# SPDX-License-Identifier: GPL-3.0-or-later

cmake_minimum_required(VERSION 3.25)
project(squish)

if(NOT SOURCE_DIR)
	message(FATAL_ERROR "SOURCE_DIR must be defined.")
endif()

file(
	GLOB files
	LIST_DIRECTORIES false
	${SOURCE_DIR}/*.cpp
	${SOURCE_DIR}/*.h
)

source_group(TREE ${SOURCE_DIR} FILES ${files})

add_library(${PROJECT_NAME} ${files})

target_include_directories(
	${PROJECT_NAME}
	PUBLIC
		$<BUILD_INTERFACE:${SOURCE_DIR}>
		$<INSTALL_INTERFACE:include>
)
