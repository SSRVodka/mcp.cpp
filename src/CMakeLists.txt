set(TARGET mcp)

aux_source_directory(${CMAKE_CURRENT_SOURCE_DIR} SRC_DIR)

if (BUILD_SHARED_LIBS)
    add_library(${TARGET} SHARED ${SRC_DIR})
else()
    add_library(${TARGET} STATIC ${SRC_DIR})
endif()

target_include_directories(${TARGET} PUBLIC ../include)

target_link_libraries(${TARGET} PUBLIC ${CMAKE_THREAD_LIBS_INIT})

# If OpenSSL is found, link the OpenSSL libraries
if(OPENSSL_FOUND)
    target_link_libraries(${TARGET} PUBLIC ${OPENSSL_LIBRARIES})
endif()
