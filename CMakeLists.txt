cmake_minimum_required(VERSION 3.11)

project(posix_demo C)

include(FetchContent)

FetchContent_Declare( freertos_kernel
  GIT_REPOSITORY https://github.com/FreeRTOS/FreeRTOS-Kernel.git
  GIT_TAG        c1980cedb110e3826fbf22d93fccaa2ca3d9daf8 #Note: Best practice to use specific git-hash or tagged version
)

add_library(freertos_config INTERFACE)

target_include_directories(freertos_config SYSTEM
INTERFACE
    include
)

target_compile_definitions(freertos_config
  INTERFACE
    projCOVERAGE_TEST=0
)

set( FREERTOS_HEAP "3" CACHE STRING "" FORCE)
set( FREERTOS_PORT "GCC_POSIX" CACHE STRING "" FORCE)

FetchContent_MakeAvailable(freertos_kernel)

# Create executable with demo code files
add_executable(${PROJECT_NAME}
    main.c
    console.c
)

target_link_libraries(${PROJECT_NAME} freertos_kernel)
