cmake_minimum_required(VERSION 3.15)
project(test_package LANGUAGES CXX)

find_package(spdlog REQUIRED CONFIG)

add_executable(${PROJECT_NAME} test_package.cpp)
if(SPDLOG_HEADER_ONLY)
    target_link_libraries(${PROJECT_NAME} PUBLIC spdlog::spdlog_header_only)
else()
    target_link_libraries(${PROJECT_NAME} PUBLIC spdlog::spdlog)
endif()

if(SPDLOG_USE_STD_FORMAT)
    target_compile_features(${PROJECT_NAME} PRIVATE cxx_std_20)
else()
    target_compile_features(${PROJECT_NAME} PRIVATE cxx_std_11)
endif()
