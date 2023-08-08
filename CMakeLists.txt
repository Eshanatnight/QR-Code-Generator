cmake_minimum_required(VERSION 3.20)
project(QR_Code_Generator)

set(CMAKE_CXX_STANDARD 20)

add_executable(QR_Code_Generator src/main.cpp src/qrcodegen.cpp src/qrcodegen.h)
