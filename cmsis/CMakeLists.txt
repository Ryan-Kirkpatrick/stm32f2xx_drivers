add_library(cmsis
    src/system_stm32f2xx.c
)

target_include_directories(cmsis PUBLIC inc)



# Check that the target MCU platform is set
if(MCU_TYPE STREQUAL "STM32F205xx")
elseif(MCU_TYPE STREQUAL "STM32F215xx")
elseif(MCU_TYPE STREQUAL "STM32F207xx")
elseif(MCU_TYPE STREQUAL "STM32F217xx")
else()
    message(FATAL_ERROR "MCU_TYPE not set or invalid. Must be one of: STM32F205xx, STM32F215xx, STM32F207xx, STM32F217xx")
endif()

# Add compile definition
target_compile_definitions(cmsis PUBLIC ${MCU_TYPE})

add_library(stm32f2xx_drivers::cmsis ALIAS cmsis)


