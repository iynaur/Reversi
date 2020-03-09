# Set the minimum version of cmake required to build this project
cmake_minimum_required(VERSION 2.6)
# Set the name and the supported language of the project
project(Reversi C)

set(CMAKE_C_STANDARD 99)

add_compile_options("$<$<C_COMPILER_ID:MSVC>:/utf-8>")
add_compile_options("$<$<CXX_COMPILER_ID:MSVC>:/utf-8>")

# Use the package PkgConfig to detect GTK+ headers/library files
#find_package(PkgConfig REQUIRED)
#pkg_check_modules(GTK3 REQUIRED gtk+-3.0)

# Setup CMake to use GTK+, tell the compiler where to look for headers
# and to the linker where to look for libraries
include_directories("E:\vcpkg\installed\x64-windows\include")
message(status " GTK3_INCLUDE_DIRS = ${GTK3_INCLUDE_DIRS}")
link_directories("E:\vcpkg\installed\x64-windows\lib")
message(status " GTK3_LIBRARY_DIRS = ${GTK3_LIBRARY_DIRS}")

# Add other flags to the compiler
add_definitions(${GTK3_CFLAGS_OTHER})
message(status " GTK3_CFLAGS_OTHER = ${GTK3_CFLAGS_OTHER}")

# Add an executable compiled from hello.c
add_executable(hello-world main.c pipes-win.c reversi.c)

# Link the target to the GTK+ libraries
target_link_libraries(hello-world "gtk-3.0.lib")
target_link_libraries(hello-world "gdk-3.0.lib")
target_link_libraries(hello-world "glib-2.0.lib")
target_link_libraries(hello-world "gobject-2.0.lib")
target_link_libraries(hello-world "gio-2.0.lib")



message(status " GTK3_LIBRARIES = ${GTK3_LIBRARIES}")

message(status " pkgs_cflags = ${PKGS_CFLAGS}")