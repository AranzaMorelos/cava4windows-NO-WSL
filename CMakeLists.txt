#This shit was made with AI, tears and a dream I guess
cmake_minimum_required(VERSION 3.13)
project(cava)

set(LIBS_DIR "C:/Users/aranz/Yakult/libs")
set(VCPKG_DIR "C:/Users/aranz/Yakult/vcpkg/installed/x64-windows")

include_directories(
    "${LIBS_DIR}/sdl2/include"
    "${LIBS_DIR}/glew/include"
    "${VCPKG_DIR}/include"
    "${CMAKE_CURRENT_SOURCE_DIR}"
    "${CMAKE_CURRENT_SOURCE_DIR}/thirdparty"
    "${CMAKE_CURRENT_SOURCE_DIR}/input"
    "${CMAKE_CURRENT_SOURCE_DIR}/output"
)

# LISTA ACTUALIZADA: Quitamos iniparser/dictionary y dejamos el núcleo nuevo
set(SOURCES
    "cava.c"
    "cavacore.c"
    "config.c"
    "input/common.c"
    "input/winscap.c"
    "output/sdl_cava.c"
    "output/sdl_glsl.c"
    "output/terminal_noncurses.c"
    "output/raw.c"
    "output/noritake.c"
)

add_executable(cava ${SOURCES})

target_compile_definitions(cava PRIVATE WIN32 SDL SDL_GSL NDEBUG SDL_MAIN_HANDLED)

target_link_libraries(cava PRIVATE 
    "${LIBS_DIR}/sdl2/lib/x64/SDL2.lib"
    "${LIBS_DIR}/sdl2/lib/x64/SDL2main.lib"
    "${LIBS_DIR}/glew/lib/Release/x64/glew32.lib"
    "${VCPKG_DIR}/lib/fftw3.lib"
    "${VCPKG_DIR}/lib/pthreadVC3.lib"
    shlwapi ws2_32 advapi32 user32 shell32 ole32 opengl32
)
