cmake_minimum_required(VERSION 3.19)
project(HiAI LANGUAGES CXX)

find_package(Qt6 6.5 REQUIRED COMPONENTS Core Widgets)

qt_standard_project_setup()

qt_add_executable(HiAI
    WIN32 MACOSX_BUNDLE
    main.cpp
    appwindow.cpp
    appwindow.h
    appwindow.ui
)

target_link_libraries(HiAI
    PRIVATE
        Qt::Core
        Qt::Widgets
)

install(TARGETS HiAI
    BUNDLE  DESTINATION .
    RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
)

qt_generate_deploy_app_script(
    TARGET HiAI
    OUTPUT_SCRIPT deploy_script
    NO_UNSUPPORTED_PLATFORM_ERROR
)
install(SCRIPT ${deploy_script})
