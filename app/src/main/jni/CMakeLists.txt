project(ncnnyolox)

cmake_minimum_required(VERSION 3.10)

INCLUDE_DIRECTORIES(${CMAKE_SOURCE_DIR}/eigen-3.3.9)

set(OpenCV_DIR ${CMAKE_SOURCE_DIR}/opencv-mobile-4.5.4-android/sdk/native/jni)
find_package(OpenCV REQUIRED core imgproc)

set(ncnn_DIR ${CMAKE_SOURCE_DIR}/ncnn-20211208-android-vulkan/${ANDROID_ABI}/lib/cmake/ncnn)
find_package(ncnn REQUIRED)

add_library(ncnnyolox SHARED yoloxncnn.cpp yolox.cpp ndkcamera.cpp BYTETracker.cpp kalmanFilter.cpp lapjv.cpp STrack.cpp utils.cpp)

target_link_libraries(ncnnyolox ncnn ${OpenCV_LIBS} camera2ndk mediandk)
