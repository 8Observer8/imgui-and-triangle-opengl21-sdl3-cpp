[Building ImGUI statically and setting up it to the CMake project](https://8observer8.github.io/tutorials/setting-up/sdl3-for-windows/public/index.html#building-imgui-statically)

> mkdir dist\win

> cd dist

> cmake -G "MinGW Makefiles" --fresh -S .. -B ..\dist\win -DSDL3_DIR=E:\libs\sdl3-desktop-prefix\lib\cmake\SDL3

> cd win

> mingw32-make

> app

![alt text](https://raw.githubusercontent.com/8Observer8/imgui-and-triangle-opengl21-sdl3-cpp/main/screenshots/imgui-and-triangle-opengl21-sdl3-cpp.png "Title")
