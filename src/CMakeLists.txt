# The Flutter tooling requires that developers have CMake 3.10 or later
# installed. You should not increase this version, as doing so will cause
# the plugin to fail to compile for some customers of the plugin.
cmake_minimum_required(VERSION 3.10)

project(libowa_flutter_library VERSION 0.0.1 LANGUAGES C)

add_library(oswrapper_audio SHARED
  "oswrapper_audio.c"
)

if(WIN32)
    target_link_libraries(oswrapper_audio PRIVATE mfplat.lib mfreadwrite.lib shlwapi.lib )
elseif(APPLE)
    target_link_libraries(oswrapper_audio PRIVATE -Framework AudioToolbox)
else()
    message("This library won't work in this platform!")
endif()

