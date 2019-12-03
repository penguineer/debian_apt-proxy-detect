# Create a dist tarball
#
# Call as:
#           make package

# Must be set before the project directive!
set(CMAKE_INSTALL_PREFIX "/usr")

set(CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake/modules ${CMAKE_MODULE_PATH})


project(apt-proxy-detect)

cmake_minimum_required(VERSION 3.13)


file(GLOB apt_files
    "01proxy"
)

file(GLOB doc_files
    "README.md"
    "LICENSE.txt"
)

file(GLOB script_files
    "apt-proxy-detect.sh"
)

file(GLOB deps
    ${apt_files}
    ${doc_files}
    ${script_files}
)


install(FILES ${apt_files} DESTINATION /etc/apt/apt.conf.d)
install(FILES ${doc_files} DESTINATION ${CMAKE_INSTALL_PREFIX}/share/doc/${CMAKE_PROJECT_NAME})
install(FILES ${script_files} DESTINATION ${CMAKE_INSTALL_PREFIX}/lib/${CMAKE_PROJECT_NAME})

add_custom_target(package
    DEPENDS ${deps}

    COMMAND rm -rf ${CMAKE_BINARY_DIR}/output

    COMMAND make install DESTDIR=${CMAKE_BINARY_DIR}/output

    COMMAND tar cjvf ${CMAKE_PROJECT_NAME}.tar.bz2 -C ${CMAKE_BINARY_DIR}/output .
)
