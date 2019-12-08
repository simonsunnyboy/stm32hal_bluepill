# CMake Build script for the STM32 Cube Firmware for use with STM32F103C8 "Blue Pill"

(c) 2019 by Matthias Arndt <marndt@asmsoftware.de>

The MIT License applies. See LICENSE for details.


## Abstract

This is a build script to compile the STM32 HAL drivers once into a static library for reuse on STm32 "Blue pill" projects.

## System requirements

- arm-none-eabi compiler toolchain
- CMake
- STM32 Cube Firmware (as downloaded through the STM32 CubeMX software)

## Configuration

A basic library configuration header for all features is included.

The resulting library can be linked with any other project without having to recompile from source.

## CMake invocation

The CMakeLists.txt should be setup to use the arm-none-eabi GNU toolchain.
It is recommended to use a suitable toolchain description file for CMake.

The author uses https://github.com/vpetrigo/arm-cmake-toolchains in particular.
