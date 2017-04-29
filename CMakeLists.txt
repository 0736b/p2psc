cmake_minimum_required(VERSION 3.6)
project(p2psc)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Werror -Wno-missing-braces -std=c++14")

add_library(p2psc
        include/p2psc/key/keypair.h
        include/p2psc/key/public_key.h
        include/p2psc/connection.h
        include/p2psc/mediator.h
        include/p2psc/peer.h

        src/connection.cpp)

target_include_directories(p2psc PUBLIC include)

add_subdirectory(test)
add_subdirectory(vendor/spotify-json)

target_link_libraries(p2psc spotify-json)