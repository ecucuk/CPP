# Minimum CMake versiyonu
cmake_minimum_required(VERSION 3.10)

# Proje adı
project(01_09_01_2023)

# C++17 standardını kullan
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Çalıştırılabilir dosyayı oluştur
add_executable(${PROJECT_NAME} main.cpp)