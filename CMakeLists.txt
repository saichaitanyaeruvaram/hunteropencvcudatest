cmake_minimum_required(VERSION 3.14)

SET( CONFIG_FILEPATH ${CMAKE_SOURCE_DIR}/cmake/config.cmake)

include("./cmake/HunterGate.cmake")
HunterGate(
	URL "https://github.com/cpp-pm/hunter/archive/v0.23.280.tar.gz"
    SHA1 "065d44b4e42e959eb5bdf1f6fdbf9c5c7c2762bd"
	FILEPATH ${CONFIG_FILEPATH}
  )

project(OPENCVHUNTERTEST LANGUAGES CXX CUDA)
hunter_add_package(OpenCV)
find_package(OpenCV)	

SET(SOURCE
	main.cpp
)

add_executable(test 
	${SOURCE}
)

target_link_libraries(test 
	${OpenCV_LIBS}
)