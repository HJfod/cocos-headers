cmake_minimum_required(VERSION 3.0.0)

project(cocos-headers CXX)

# compile empty cpp because msvc is stupid
add_library(cocos2d STATIC cocos2dx/dummy.cpp)

# really make sure its c++
set_target_properties(cocos2d PROPERTIES
  LANGUAGE CXX
  LINKER_LANGUAGE CXX
)

target_include_directories(cocos2d PUBLIC 
  cocos2dx
  cocos2dx/include
  cocos2dx/kazmath/include
  cocos2dx/platform/win32
  cocos2dx/platform/third_party/win32
  cocos2dx/platform/third_party/win32/OGLES
  extensions
)

target_link_libraries(cocos2d
  ${CMAKE_CURRENT_LIST_DIR}/cocos2dx/libcocos2d.lib
  ${CMAKE_CURRENT_LIST_DIR}/extensions/libExtensions.lib
)
