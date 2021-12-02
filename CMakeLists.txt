cmake_minimum_required(VERSION 3.13)
# Project information
project(Eigen
  VERSION 3.0.2
  DESCRIPTION "Eigen matrix math library."
  LANGUAGES CXX
)
# Add the library target
add_library(eigen INTERFACE)
# Setup include directories 
target_include_directories(eigen INTERFACE src/)

# Example and unit testing if this project is built separately
if (PROJECT_NAME STREQUAL CMAKE_PROJECT_NAME)
	# Add the example target
	add_executable(eigen_example examples/cmake/eigen_example.cc)
	# Add the includes
	target_include_directories(eigen_example PUBLIC 
		$<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
		$<INSTALL_INTERFACE:include>
	)
	# Link libraries to the example target
	target_link_libraries(eigen_example
		PRIVATE 
			eigen
	)
endif()
