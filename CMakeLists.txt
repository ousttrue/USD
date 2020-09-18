project(usd)
cmake_minimum_required(VERSION 3.12)
set (CMAKE_ARCHIVE_OUTPUT_DIRECTORY_DEBUG ${CMAKE_BINARY_DIR}/Debug/lib)
set (CMAKE_LIBRARY_OUTPUT_DIRECTORY_DEBUG ${CMAKE_BINARY_DIR}/Debug/lib)
set (CMAKE_RUNTIME_OUTPUT_DIRECTORY_DEBUG ${CMAKE_BINARY_DIR}/Debug/bin)
set (CMAKE_ARCHIVE_OUTPUT_DIRECTORY_RELEASE ${CMAKE_BINARY_DIR}/Release/lib)
set (CMAKE_LIBRARY_OUTPUT_DIRECTORY_RELEASE ${CMAKE_BINARY_DIR}/Release/lib)
set (CMAKE_RUNTIME_OUTPUT_DIRECTORY_RELEASE ${CMAKE_BINARY_DIR}/Release/bin)

if (NOT CMAKE_SIZEOF_VOID_P EQUAL 8)
    if (WIN32)
        message(FATAL_ERROR "Compiler does not support 64-bit builds. "
                "If you are using Visual Studio, make sure you are in the "
                "x64 command prompt and have specified the Win64 cmake "
                "generator (e.g., -G \"Visual Studio 14 2015 Win64\")")
    else()
        message(FATAL_ERROR "Compiler does not support 64-bit builds.")
    endif()
endif()

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH}
                      ${CMAKE_SOURCE_DIR}/cmake/defaults
                      ${CMAKE_SOURCE_DIR}/cmake/modules
                      ${CMAKE_SOURCE_DIR}/cmake/macros)

include(Options)
include(ProjectDefaults)
# include(Packages)
set(Boost_INCLUDE_DIRS $ENV{VCPKG_DIR}/installed/x64-windows/include)
set(PYTHON_LIBRARIES 
    C:/Python38/libs/python38.lib
    $ENV{VCPKG_DIR}/installed/x64-windows/lib/boost_python38-vc140-mt.lib
    )
link_directories(
DEBUG $ENV{VCPKG_DIR}/installed/x64-windows/debug/lib
OPTIMIZED $ENV{VCPKG_DIR}/installed/x64-windows/lib)

# # This has to be defined after Packages is included, because it relies on the
# # discovered path to the python executable.
# set(PXR_PYTHON_SHEBANG "${PYTHON_EXECUTABLE}" 
#     CACHE 
#     STRING
#     "Replacement path for Python #! line."
# )

# CXXDefaults will set a variety of variables for the project.
# Consume them here. This is an effort to keep the most common
# build files readable.
include(CXXDefaults)
add_definitions(${_PXR_CXX_DEFINITIONS})
set(CMAKE_CXX_FLAGS "${_PXR_CXX_FLAGS} ${CMAKE_CXX_FLAGS}")
include(Public)

pxr_toplevel_prologue()
pxr_core_prologue()

include_directories(
    ${CMAKE_CURRENT_LIST_DIR}
    ${CMAKE_BINARY_DIR}/include
    ${Boost_INCLUDE_DIRS}
    C:/Python38/include
    )

subdirs(
    pxr/base/arch
    pxr/base/tf
    pxr/base/gf
    pxr/base/js
    pxr/base/trace
    pxr/base/work
    # pxr/base/plug
    # pxr/base/vt
)
# add_subdirectory(pxr)
# add_subdirectory(extras)

# if (PXR_BUILD_PRMAN_PLUGIN)
#     set(prmanPluginPath "third_party/renderman-${RENDERMAN_VERSION_MAJOR}")

#     get_filename_component(prmanPluginAbsPath "${prmanPluginPath}" ABSOLUTE)
#     if (EXISTS "${prmanPluginAbsPath}")
#         add_subdirectory("${prmanPluginPath}")
#     else()
#         message(FATAL_ERROR "No RenderMan plugin available for "
#                 "RenderMan ${RENDERMAN_VERSION_MAJOR}")
#     endif()
# endif()

# if (PXR_BUILD_DOCUMENTATION)
#     pxr_build_documentation()
# endif()   

# pxr_toplevel_epilogue()
