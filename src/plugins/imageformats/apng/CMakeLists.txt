cmake_minimum_required(VERSION 3.13)

set(plugin apng)

set(CMAKE_AUTOMOC ON)

find_package(Qt6 REQUIRED COMPONENTS Gui)

qt_add_plugin(${plugin} PLUGIN_TYPE imageformats)
target_sources(${plugin} PRIVATE
    apngimageplugin.h
    apngreader_p.h
    apngimagehandler_p.h
    apngimageplugin.cpp
    apngimagehandler.cpp
    apngreader.cpp
)
set_target_properties(${plugin} PROPERTIES OUTPUT_NAME "qtapng")
target_link_libraries(${plugin} PRIVATE Qt6::Gui vendored_libpng)
install(TARGETS ${plugin} DESTINATION ${KDE_INSTALL_QTPLUGINDIR}/imageformats)