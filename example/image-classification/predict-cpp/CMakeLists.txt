if(USE_OPENCV)
  find_package(OpenCV QUIET COMPONENTS core highgui imgproc imgcodecs)
  if(NOT OpenCV_FOUND) # if not OpenCV 3.x, then imgcodecs are not found
    find_package(OpenCV REQUIRED COMPONENTS core highgui imgproc)
  endif()
  add_executable(image-classification-predict image-classification-predict.cc)
  include_directories(SYSTEM ${OpenCV_INCLUDE_DIRS})
  target_link_libraries(image-classification-predict mxnet)
  target_link_libraries(image-classification-predict ${OpenCV_LIBS})
  list(APPEND mxnet_LINKER_LIBS ${OpenCV_LIBS})
endif()

