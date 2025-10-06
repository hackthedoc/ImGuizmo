cmake_minimum_required(VERSION 3.16)
project(ImGuizmo)

# ImGuizmo source files
set(IMGUI_SOURCES
    GraphEditor.cpp
    ImCurveEdit.cpp
    ImGradient.cpp
    ImGuizmo.cpp
    ImSequencer.cpp
)

# ImGuizmo include directories
set(IMGUI_INCLUDES
    GraphEditor.h
    ImCurveEdit.h
    ImGradient.h
    ImGuizmo.h
    ImSequencer.h
    ImZoomSlider.h
)

# Create static library
add_library(ImGuizmo STATIC ${IMGUI_SOURCES})
target_include_directories(ImGuizmo PUBLIC ${IMGUI_INCLUDES})

# C++17 standard
target_compile_features(ImGuizmo PUBLIC cxx_std_17)

# Platform defines
if(WIN32)
    target_compile_definitions(ImGuizmo PUBLIC _CRT_SECURE_NO_WARNINGS)
endif()
