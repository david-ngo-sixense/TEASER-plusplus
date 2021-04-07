cmake_minimum_required(VERSION 3.10)
project(teaser_cpp_ply)

set(CMAKE_CXX_STANDARD 17)

find_package(Eigen3 REQUIRED)

set(teaser_DIR "C:/dev/TEASER-plusplus/teaser/include")
set(teaser_IO_LIB "C:/dev/TEASER-plusplus/build/teaser/Release/teaser_io.lib")
set(teaser_REGISTRATION_LIB "C:/dev/TEASER-plusplus/build/teaser/Release/teaser_registration.lib")
include_directories(${teaser_DIR})
#find_package(teaserpp REQUIRED)

# Change this line to include your own executable file
add_executable(teaser_cpp_ply teaser_cpp_ply.cc)

# Link to teaserpp & Eigen3
target_link_libraries(teaser_cpp_ply Eigen3::Eigen  ${teaser_REGISTRATION_LIB} ${teaser_IO_LIB})

# Copy the data files to build directory
file(COPY ../example_data/
        DESTINATION ./example_data/
        FILES_MATCHING
        PATTERN *.ply)
