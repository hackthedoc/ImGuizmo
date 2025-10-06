cmake_minimum_required(VERSION 3.16)
project(ImGuizmo)

# ----------------------------
# ImGuizmo source files
# ----------------------------
set(IMGUIZMO_SOURCES
    GraphEditor.cpp
    ImCurveEdit.cpp
    ImGradient.cpp
    ImGuizmo.cpp
    ImSequencer.cpp
)

# ----------------------------
# Create static library
# ----------------------------
add_library(ImGuizmo STATIC ${IMGUIZMO_SOURCES})

# ----------------------------
# Include directories
# ----------------------------
target_include_directories(ImGuizmo PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}              # ImGuizmo headers
    ${CMAKE_CURRENT_SOURCE_DIR}/../imgui     # ImGui headers
    ${CMAKE_CURRENT_SOURCE_DIR}/../imgui/backends
)

# ----------------------------
# C++ standard and platform defines
# ----------------------------
target_compile_features(ImGuizmo PUBLIC cxx_std_17)

if (WIN32)
    target_compile_definitions(ImGuizmo PUBLIC _CRT_SECURE_NO_WARNINGS)
endif()

# ----------------------------
# Link dependencies
# ----------------------------
target_link_libraries(ImGuizmo PUBLIC ImGui)
