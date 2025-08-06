cmake_minimum_required(VERSION 3.10)
project(rtklib)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/rtklib)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/rtklib/src)

# Add source files
file(GLOB SRC ${PROJECT_SOURCE_DIR}/rtklib/src/*.c
              ${PROJECT_SOURCE_DIR}/rtklib/src/rcv/*.c
              ${PROJECT_SOURCE_DIR}/rtklib/src/*.cpp)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin)

add_definitions(-DWIN32 -D_WIN_DLL)

add_executable(rnx2rtkp ${SRC})

if(WIN32)
    target_link_libraries(rnx2rtkp  ws2_32 winmm pthread)
else(UNIX)
endif()
