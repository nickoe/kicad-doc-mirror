# List of variables that may be set from command line:
#
# CMAKE_VERBOSE_MAKEFILE ON/OFF (OPTIONAL)
#   Turns ON/OFF verbose build messages.
#   You can also pass VERBOSE=1 to make for the same effect.
#
# CMAKE_INSTALL_PREFIX (OPTIONAL)
#
#
# Our project is called 'kicad'. This is what it will be called in
# our makefiles.
project(kicad)

cmake_minimum_required(VERSION 2.4.6 FATAL_ERROR)

# Locations for install targets.
if(UNIX)
    if(APPLE)
    else(APPLE)
        # Like all variables, CMAKE_INSTALL_PREFIX can be over-ridden on the command line.
        set(CMAKE_INSTALL_PREFIX /usr/local CACHE PATH "")
        # When used later, "bin" and others with no leading / is relative to CMAKE_INSTALL_PREFIX.
        set(KICAD_DOCS share/doc/kicad CACHE PATH "Location of KiCad documentation files.")
        set(KICAD_HELP share/doc/kicad/help CACHE PATH "Location of KiCad help files.")
    endif(APPLE)
endif(UNIX)

if(WIN32)
    # Like all variables, CMAKE_INSTALL_PREFIX can be over-ridden on the command line.
    set(CMAKE_INSTALL_PREFIX c:/kicad CACHE PATH "")
    # When used later, "winexe" and others with no leading / is relative to CMAKE_INSTALL_PREFIX.
    set(KICAD_DOCS doc)
    set(KICAD_HELP ${KICAD_DOCS}/help)
endif(WIN32)

# CMake will look in these dirs for nested 'CMakeLists.txt' files.
# Resources.
add_subdirectory(doc)
