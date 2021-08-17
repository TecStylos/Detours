cmake_minimum_required(VERSION 3.8)

project("Detours")

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED TRUE)

add_library(
    Detours STATIC
    "src/creatwth.cpp"
    "src/detours.cpp"
    "src/detours.h"
    "src/detver.h"
    "src/disasm.cpp"
    "src/disolarm.cpp"
    "src/disolarm64.cpp"
    "src/disolia64.cpp"
    "src/disolx64.cpp"
    "src/disolx86.cpp"
    "src/image.cpp"
    "src/modules.cpp"
    "src/uimports.cpp"
)

set_property (
    SOURCE "src/uimports.cpp"
    APPEND PROPERTY HEADER_FILE_ONLY true
)

target_compile_options(
    Detours PRIVATE
    /W4 /WX /Zi /MT /Gy /Gm- /Zl /Od
)

target_include_directories(
    Detours PUBLIC
    "src"
)

add_executable(
    withdll
    "samples/withdll/withdll.cpp"
)
target_link_libraries(
    withdll
    Detours
)