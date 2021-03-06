cmake_minimum_required(VERSION 3.6)
project(p2psc)
enable_testing()

set(CMAKE_CXX_FLAGS
        "${CMAKE_CXX_FLAGS} -Wall -Werror -Wno-unused-variable -Wno-sign-compare -Wno-missing-braces -Wno-unused-function -std=c++14")

add_library(p2psc
        include/p2psc.h
        include/p2psc/connection.h
        include/p2psc/connection_exception.h
        include/p2psc/crypto/crypto_exception.h
        include/p2psc/crypto/pki.h
        include/p2psc/error.h
        include/p2psc/key/keypair.h
        include/p2psc/key/public_key.h
        include/p2psc/log.h
        include/p2psc/mediator.h
        include/p2psc/message/message.h
        include/p2psc/message/advertise.h
        include/p2psc/message/advertise_abort.h
        include/p2psc/message/advertise_challenge.h
        include/p2psc/message/advertise_response.h
        include/p2psc/message/advertise_retry.h
        include/p2psc/message/anonymous_message_format.h
        include/p2psc/message/message_decoder.h
        include/p2psc/message/message_exception.h
        include/p2psc/message/message_format.h
        include/p2psc/message/message_util.h
        include/p2psc/message/peer_acknowledgement.h
        include/p2psc/message/peer_challenge.h
        include/p2psc/message/peer_challenge_response.h
        include/p2psc/message/peer_disconnect.h
        include/p2psc/message/peer_identification.h
        include/p2psc/message/peer_response.h
        include/p2psc/message/types.h
        include/p2psc/peer.h
        include/p2psc/punched_peer.h
        include/p2psc/socket_creator.h
        include/p2psc/socket/socket.h
        include/p2psc/socket/socket_address.h
        include/p2psc/socket/socket_exception.h
        include/p2psc/version.h

        src/connection.cpp
        src/crypto/rsa.cpp
        src/key/keypair.cpp
        src/key/public_key.cpp
        src/mediator_connection.cpp
        src/socket/local_listening_socket.cpp
        src/socket/socket.cpp)

target_include_directories(p2psc
        PUBLIC
        include
        PRIVATE
        src)

add_subdirectory(test)
add_subdirectory(integration)
add_subdirectory(vendor/spotify-json)
add_subdirectory(vendor/base64)

target_link_libraries(p2psc spotify-json boost_system crypto pthread)