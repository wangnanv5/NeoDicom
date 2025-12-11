cmake_minimum_required(VERSION 4.0)
project(qt_vtk)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

if(MSVC)
    add_compile_options("/utf-8")
endif()

find_package(VTK COMPONENTS CommonCore GUISupportQt)
if (NOT VTK_FOUND)
    message("Skipping example: ${VTK_NOT_FOUND_MESSAGE}")
    return ()
endif ()

#find_package("Qt${VTK_QT_VERSION}" COMPONENTS Core Widgets)
#if (NOT TARGET "Qt${VTK_QT_VERSION}::Core" OR NOT TARGET "Qt${VTK_QT_VERSION}::Widgets")
#    message("Skipping example: ${Qt${VTK_QT_VERSION}_NOT_FOUND_MESSAGE}")
#    return ()
#endif ()
#set(CMAKE_AUTOMOC ON)
#set(CMAKE_AUTOUIC ON)

# Set your files and resources here
set(Sources main.cpp)

set(Headers header/image.h)

# Instruct CMake to run moc automatically when needed.

# CMAKE_AUTOMOC in ON so the MocHdrs will be automatically wrapped.
add_executable(NeoDicom ${Sources} ${Headers})
target_link_libraries(NeoDicom
        PRIVATE
        ${NeoDicom}
        #        "Qt${VTK_QT_VERSION}::Core"
        #        "Qt${VTK_QT_VERSION}::Widgets"
)

vtk_module_autoinit(
        TARGETS NeoDicom
        MODULES ${VTK_LIBRARIES}
)
