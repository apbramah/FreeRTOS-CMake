# FreeRTOS-CMake

This repository covers the use of FreeRTOS with CMake.

The goal is to use the [Posix/Linux Simulator Demo for FreeRTOS](https://www.freertos.org/FreeRTOS-simulator-for-Linux.html) in order to run FreeRTOS on Linux. This work is based on the [Posix GCC Demo](https://github.com/FreeRTOS/FreeRTOS/tree/master/FreeRTOS/Demo/Posix_GCC) of FreeRTOS. 

## Prerequisites
- GNU Make 4.1
- CMake version 3.10.2
- GCC 7.5.0

Tested on Ubuntu 18.04 Lts distribution with Windows WSL.

## Project structure
Project is a simple demo responsible to create two tasks communicating with queue and triggered by timers. It will print received messages in the console.
- [main.c](main.c) contains application code
- [console.h/c](console.h) are used to trace code by avoiding concurrency issues
- [include/FreeRTOSConfig.h](FreeRTOSConfig.h) is need by FreeRTOS. It contains application specific definitions that are adjusted for a particular hardware and application requirements. This one comes from the [POSIX demo](https://github.com/FreeRTOS/FreeRTOS/blob/master/FreeRTOS/Demo/Posix_GCC/FreeRTOSConfig.h).
- [CMakeLists.txt](CMakeLists.txt) used by CMake

## CMake usage

Build the example with:

```
❯ mkdir build && cd build && cmake .. && make
```

And run it with:
```
❯ ./posix_demo
Starting echo blinky demo
Message received from task
Message received from software timer
Message received from task
Message received from task
Message received from software timer
Message received from task
```

