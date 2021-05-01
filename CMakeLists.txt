cmake_minimum_required(VERSION 3.13)
# Project information
project(Eigen
  VERSION 2.0.0
  DESCRIPTION "Eigen matrix math library."
  LANGUAGES CXX
)
# Add the library target
add_library(eigen INTERFACE)
# Setup include directories 
target_include_directories(eigen INTERFACE include/)
