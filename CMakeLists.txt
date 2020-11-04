cmake_minimum_required(VERSION 3.14)

SET( CONFIG_FILEPATH ${CMAKE_SOURCE_DIR}/cmake/config.cmake)

include("./cmake/HunterGate.cmake")
HunterGate(
	URL "https://github.com/saichaitanyaeruvaram/hunter/archive/opencv-4.5.0.tar.gz"
    SHA1 "1258e48a1c06ce027b6d3aa141c7f9661ff0d843"
	FILEPATH ${CONFIG_FILEPATH}
  )

project(OPENCVHUNTERTEST)
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