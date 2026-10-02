cmake_minimum_required(VERSION 3.4.1)
project(VINSMobile)

# done here so it's not necessary for every target_link_library call of opencv
if(NOT OpenCV_FOUND)
  if(NOT OpenCV_DIR)
    SET(OpenCV_DIR $ENV{OPENCV_SDK_PATH})
  endif()
  find_package(OpenCV REQUIRED)
endif()

# this is branching into all the subdirectories and thus connecting them all
add_subdirectory(VINS_ThirdPartyLib)
add_subdirectory(ThirdParty/DBoW)
add_subdirectory(ThirdParty/DUtils)
add_subdirectory(ThirdParty/DVision)
add_subdirectory(VINS_ios)