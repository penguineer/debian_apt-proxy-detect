project(apt-proxy-detect)

cmake_minimum_required(VERSION 3.13)


file(GLOB apt_files
    "01proxy"
)

file(GLOB share_files
    "README.md"
    "LICENSE.txt"
)

file(GLOB script_files
    "apt-proxy-detect.sh"
)

file(GLOB deps
    ${apt_files}
    ${share_files}
    ${script_files}
)

include(GNUInstallDirs)

install(FILES ${apt_files} DESTINATION ${CMAKE_INSTALL_FULL_SYSCONFDIR}/apt/apt.conf.d)
install(FILES ${share_files} DESTINATION ${CMAKE_INSTALL_FULL_DOCDIR})
install(FILES ${script_files} DESTINATION ${CMAKE_INSTALL_FULL_LIBEXECDIR}/${CMAKE_PROJECT_NAME})
