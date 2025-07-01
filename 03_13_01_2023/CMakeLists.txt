# Minimum CMake versiyonu
cmake_minimum_required(VERSION 3.10)

# Proje adı
project(02_13_01_2023)

# C++17 standardını kullan
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Çalıştırılabilir dosyayı oluştur
add_executable(${PROJECT_NAME} main.cpp)

set_target_properties(${PROJECT_NAME} PROPERTIES
    RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/bin")