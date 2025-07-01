cmake_minimum_required(VERSION 3.20)
project(AllExperiments LANGUAGES CXX)

# Ortak derleyici ayarları
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

# Proje dizinini ayarla
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_SOURCE_DIR}/bin")
file(GLOB CHILD_DIRS CONFIGURE_DEPENDS
     RELATIVE "${CMAKE_SOURCE_DIR}" "[0-9][0-9]_*")   # 01_… 02_… kalıbı
foreach(dir ${CHILD_DIRS})
    if(IS_DIRECTORY "${dir}")
        add_subdirectory("${dir}")
    endif()
endforeach()