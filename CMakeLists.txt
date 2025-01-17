project(node-editor)
cmake_minimum_required(VERSION 2.6)

set(CMAKE_VERBOSE_MAKEFILE on)
set(CMAKE_CXX_COMPILER $ENV{CXX})
set(CMAKE_CXX_FLAGS "-O3 -std=c++17 -DNDEBUG")

include_directories(/usr/include/SDL2 ../nb /usr/local/include . ./imgui ./example ./imgui/backends ./imgui/misc/cpp ./imnodes ./ImGuiFileDialog)
link_directories(/usr/local/lib)

add_executable(node-editor
    imgui/imgui.cpp
    imgui/imgui_demo.cpp
    imgui/imgui_draw.cpp
    imgui/imgui_tables.cpp
    imgui/imgui_widgets.cpp
    imgui/backends/imgui_impl_opengl3.cpp
    imgui/backends/imgui_impl_sdl.cpp
    imgui/misc/cpp/imgui_stdlib.cpp
    node-editor/color_node_editor.cpp
    node-editor/main.cpp
    imnodes/imnodes.cpp
    ../nb/convert.cpp
    ../nb/File.cpp
    ImGuiFileDialog/ImGuiFileDialog.cpp)
target_link_libraries(node-editor SDL2 SDL2main GL)

install(TARGETS node-editor RUNTIME DESTINATION bin)