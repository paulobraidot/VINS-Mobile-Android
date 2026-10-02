set(TARGET_NAME VINS_Android)
set(${TARGET_NAME}_SRCS
    ViewController.cpp
)

if(NOT OpenCV_FOUND)
  if(NOT OpenCV_DIR)
    SET(OpenCV_DIR $ENV{OPENCV_SDK_PATH})
  endif()
  find_package(OpenCV REQUIRED)
endif()
set(OpenCV_LIBS opencv_java)

add_library(
    ${TARGET_NAME}
    STATIC
    ${${TARGET_NAME}_SRCS}
)

target_link_libraries( 
    ${TARGET_NAME}
    VINSMobile
    android
    log
    ${OpenCV_LIBS}
)

target_include_directories(${TARGET_NAME} INTERFACE ${CMAKE_CURRENT_SOURCE_DIR})