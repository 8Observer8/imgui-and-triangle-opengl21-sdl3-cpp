cmake_minimum_required(VERSION 3.20)

project(imgui_and_triangle)
add_executable(app) # WIN32 - add this to hide the console like this: add_executable(app WIN32)

target_include_directories(app PRIVATE E:/libs/glad-2.0.6/include)
target_include_directories(app PRIVATE E:/libs/imgui-1.91.1-sdl3-opengl3/include)

target_sources(app
PRIVATE
    E:/libs/glad-2.0.6/src/glad.c
    E:/libs/imgui-1.91.1-sdl3-opengl3/src/imgui_impl_opengl3.cpp
    E:/libs/imgui-1.91.1-sdl3-opengl3/src/imgui_impl_sdl3.cpp
    main.cpp
)

# This code copies the "SDL3.dll" file to the build directory
add_custom_command(TARGET app POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_if_different
    $<TARGET_RUNTIME_DLLS:app> $<TARGET_FILE_DIR:app>
)

find_package(SDL3)
target_link_directories(app PRIVATE E:/libs/imgui-1.91.1-sdl3-opengl3/lib)
target_link_libraries(app PRIVATE SDL3::SDL3 ImGui opengl32)

target_compile_definitions(app PRIVATE SDL_MAIN_USE_CALLBACKS)
target_link_options(app PRIVATE -static-libgcc -static-libstdc++)
