cmake_minimum_required (VERSION 3.0.0)
project(some_ip_test)

SET(CMAKE_CXX_FLAGS "-g -std=c++0x")

SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -pthread")

find_package( Boost 1.55 COMPONENTS system thread log REQUIRED )

include_directories (
    ${Boost_INCLUDE_DIR}
    ${VSOMEIP_INCLUDE_DIRS}
)

add_definitions(-DCMAKE_EXPORT_COMPILE_COMMANDS=ON)

message( ${Boost_INCLUDE_DIR})
message( ${VSOMEIP_INCLUDE_DIRS})


add_executable(service-example ./service.cpp)
add_executable(client-example ./client.cpp)

target_link_libraries(service-example vsomeip ${Boost_LIBRARIES})
target_link_libraries(client-example vsomeip ${Boost_LIBRARIES})