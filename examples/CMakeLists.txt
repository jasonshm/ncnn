macro(ncnn_add_example name)
    add_executable(${name} ${name}.cpp)
    target_include_directories(${name} PRIVATE ${OpenCV_INCLUDE_DIRS})
    target_link_libraries(${name} PRIVATE ncnn ${OpenCV_LIBS}
    )

    # add test to a virtual project group
    set_property(TARGET ${name} PROPERTY FOLDER "examples")
endmacro()

set(CMAKE_CXX_STANDARD 11)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/../src)
include_directories(${CMAKE_CURRENT_BINARY_DIR}/../src)

set (SDK30_ARMV8_DIR /home/user/cv22/cv22_linux_sdk_3.0/ambarella/prebuild/oss/armv8-a)

include_directories(
  ${SDK30_ARMV8_DIR}/opencv/include
)

find_library(OPENCV_CORE opencv_core ${SDK30_ARMV8_DIR}/opencv/usr/lib)
find_library(OPENCV_IMGCODECS opencv_imgcodecs ${SDK30_ARMV8_DIR}/opencv/usr/lib)
find_library(OPENCV_IMGPROC opencv_imgproc ${SDK30_ARMV8_DIR}/opencv/usr/lib)
find_library(OPENCV_VIDEOIO opencv_videoio ${SDK30_ARMV8_DIR}/opencv/usr/lib)
find_library(OPENCV_HIGHGUI opencv_highgui ${SDK30_ARMV8_DIR}/opencv/usr/lib)

find_library(JPEG jpeg ${SDK30_ARMV8_DIR}/libjpeg-turbo/usr/lib)
find_library(PNG png ${SDK30_ARMV8_DIR}/libpng/usr/lib)
find_library(PROTOBUF protobuf ${SDK30_ARMV8_DIR}/protobuf/usr/lib)
find_library(Z z ${SDK30_ARMV8_DIR}/zlib/usr/lib)

link_libraries(
  ${OPENCV_CORE}
  ${OPENCV_IMGCODECS}
  ${OPENCV_IMGPROC}
  ${OPENCV_VIDEOIO}
  ${OPENCV_HIGHGUI}
  ${JPEG}
  ${PNG}
  ${PROTOBUF}
  ${Z}
)

ncnn_add_example(squeezenet)
ncnn_add_example(squeezenet_c_api)
ncnn_add_example(fasterrcnn)
ncnn_add_example(rfcn)
ncnn_add_example(yolov2)
ncnn_add_example(yolov3)
ncnn_add_example(yolov4)
ncnn_add_example(yolov5)
ncnn_add_example(mobilenetv2ssdlite)
ncnn_add_example(mobilenetssd)
ncnn_add_example(squeezenetssd)
ncnn_add_example(shufflenetv2)
ncnn_add_example(peleenetssd_seg)
ncnn_add_example(simplepose)
ncnn_add_example(retinaface)
ncnn_add_example(yolact)
ncnn_add_example(nanodet)
