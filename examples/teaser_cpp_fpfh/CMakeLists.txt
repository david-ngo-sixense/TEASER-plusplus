cmake_minimum_required(VERSION 3.10)
project(teaser_cpp_fpfh)

set (CMAKE_CXX_STANDARD 17)

find_package(Eigen3 REQUIRED)

set(teaser_DIR "C:/dev/TEASER-plusplus/teaser/include")
set(teaser_IO_LIB "C:/dev/TEASER-plusplus/build/teaser/Release/teaser_io.lib")
set(teaser_REGISTRATION_LIB "C:/dev/TEASER-plusplus/build/teaser/Release/teaser_registration.lib")
set(teaser_FEATURES_LIB "C:/dev/TEASER-plusplus/build/teaser/Release/teaser_features.lib")
include_directories(${teaser_DIR})
#find_package(teaserpp REQUIRED)
find_package(Boost 1.58 REQUIRED)
find_package(PCL 1.9 REQUIRED COMPONENTS common features kdtree)

# Change this line to include your own executable file
add_executable(teaser_cpp_fpfh teaser_cpp_fpfh.cc)

# Link to teaserpp & Eigen3
target_link_libraries(teaser_cpp_fpfh Eigen3::Eigen ${teaser_FEATURES_LIB} ${teaser_REGISTRATION_LIB}
        ${teaser_IO_LIB} ${PCL_LIBRARIES})

# Copy the data files to build directory
file(COPY ../example_data/
        DESTINATION ./example_data/
        FILES_MATCHING
        PATTERN *.ply)
