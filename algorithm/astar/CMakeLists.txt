#设置CMAKE最`在这里插入代码片`低版本
CMAKE_MINIMUM_REQUIRED(VERSION 2.8.3)
#设置项目名称
SET(PROJECT_NAME OpenCV_test)
#建立项目
PROJECT(${PROJECT_NAME})
#添加OpenCV的目录
#set(OpenCV_DIR /home/test/src/opencv-3.4.10) #×××××××××××
#寻找OpenCV库
FIND_PACKAGE(OpenCV REQUIRED)
INCLUDE_DIRECTORIES(${OpenCV_INCLUDE_DIRS})
#打印调试信息
MESSAGE(STATUS "Project: ${PROJECT_NAME}")
MESSAGE(STATUS "OpenCV library status:")
MESSAGE(STATUS "    version: ${OpenCV_VERSION}")
MESSAGE(STATUS "    libraries: ${OpenCV_LIBS}")
MESSAGE(STATUS "    include path: ${OpenCV_INCLUDE_DIRS}")

#获取代码，在项目中，将所有代码都放在src文件夹中
SET(DIR_SRCS "./")
AUX_SOURCE_DIRECTORY(src DIR_SRCS)
MESSAGE(STATUS "Src file: ${DIR_SRCS}")
#编译可执行程序
ADD_EXECUTABLE(${PROJECT_NAME} ${DIR_SRCS})
#添加链接库
TARGET_LINK_LIBRARIES(${PROJECT_NAME} ${OpenCV_LIBS})