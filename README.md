# STM32 F2 Drivers

This bundles the STM32F2xx HAL and CMSIS drivers for consumption by build systems using CMake `FetchContent`.

# Usage

Use fetch content.

```cmake
# Select the MCU Type. One of:
# "STM32F205xx"
# "STM32F215xx"
# "STM32F207xx"
# "STM32F217xx"
set(MCU_TYPE "STM32F217xx")

# Set the include path for stm32f2xx_hal_conf.h
set(HAL_CONF_INCLUDE_DIR path/to/inc/for/stm32f2xx_hal_conf)

# Fetch content
FetchContent_Declare(
    stm32f2xx_drivers
    GIT_REPOSITORY https://github.com/Ryan-Kirkpatrick/stm32f2xx_drivers.git
    GIT_TAG v0.1.0
)
FetchContent_MakeAvailable(stm32f2xx_drivers)

```

This will add the `stm32f2xx_drivers::cmsis` and `stm32f2xx_drivers::hal` libraries which you may link to.

Of course you will still need to implement the HAL initialization, MSP, and HAL timebase files. See the `templates` folder for templates, or simply use the CubeIDE to generate them (recommended).
