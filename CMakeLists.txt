cmake_minimum_required(VERSION 3.13)
if (DEFINED MCU)
	# Setting up the toolchain
	set(CMAKE_TOOLCHAIN_FILE "${CMAKE_SOURCE_DIR}/cmake/cortex.cmake")
endif()
# Project information
project(Eigen
  VERSION 1.0
  DESCRIPTION "Eigen matrix math library."
  LANGUAGES CXX
)
if (DEFINED MCU)
	# Grab the processor and set up definitions and compile options
	include(${CMAKE_SOURCE_DIR}/cmake/config_mcu.cmake)
	configMcu(${MCU})
	# Fetch core
	FetchContent_Declare(
		core
		GIT_REPOSITORY 	git@gitlab.com:bolderflight/software/core.git
	)
	FetchContent_MakeAvailable(core)
  # Add the library target
  add_library(eigen INTERFACE)

	# Link libraries
	target_link_libraries(eigen
		PUBLIC
			core
	)
  # Setup include directories 
  target_include_directories(eigen INTERFACE include/)
endif()
