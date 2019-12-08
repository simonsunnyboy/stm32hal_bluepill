# 
# CMake Build script for the STM32 Cube Firmware
# for use with STM32F103C8 "Blue Pill"
#
# (c) 2019 by Matthias Arndt <marndt@asmsoftware.de>
# 
# This build script can be used under the termins of the MIT License. 
#

cmake_minimum_required(VERSION 3.10)

# points to sources of STM32 Cube Firmware to be compiled
set(STM32CUBE_FW "/opt/STM32CubeMX/Repository/STM32Cube_FW_F1_V1.8.0")

# internal variables - do not change unless ST changed the directory structure
set(HAL_BASE "${STM32CUBE_FW}/Drivers/STM32F1xx_HAL_Driver")
set(CMSIS_BASE "${STM32CUBE_FW}/Drivers/CMSIS")

set(HAL_SRC "${HAL_BASE}/Src")
set(HAL_INC "${HAL_BASE}/Inc")
set(STM32F1XX_INC "${STM32CUBE_FW}/Drivers/CMSIS/Device/ST/STM32F1xx/Include")

set(CMSIS_INC "${CMSIS_BASE}/Include")

# collect all STM32F10x HAL files for the library
file( GLOB SRCS ${HAL_SRC}/*.c ${HAL_INC}/*.h )

# configure the basic compiler flags
set(CMAKE_C_FLAGS "-std=gnu99 -g -O3 -Wall -mlittle-endian -mthumb -mthumb-interwork -mcpu=cortex-m3 -fsingle-precision-constant -Wdouble-promotion")

# set include file configuration
include_directories(
${HAL_INC}
${PROJECT_SOURCE_DIR}
${STM32F1XX_INC}
${CMSIS_INC}
)

# library targets per derivate
add_library(HAL-STM32F103xB
	${SRCS}
)

target_compile_definitions(HAL-STM32F103xB PUBLIC STM32F103xB)
