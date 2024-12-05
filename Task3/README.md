# LED Flashing System with FreeRTOS on STM32

## Description
This project is a simple implementation of LED control using FreeRTOS on an STM32 microcontroller. The program uses multiple FreeRTOS tasks to control LEDs simultaneously without interference.

There are two main tasks:
1. **FlashRedLedTask**: Controls the red LED with a fast blinking pattern.
2. **FlashGreenLedTask**: Controls the green LED with a slower blinking pattern.

## Features
- Utilizes **FreeRTOS** for multitasking.
- Independent LED control without task interference.
- GPIO-based LED on/off control on STM32.
- System clock configured using HSE with PLL.

## Hardware
This project is designed for an STM32-based board. The following pins are used:
- **LED_GREEN**: Connected to a GPIO pin on port `GPIOA`.
- **LED_RED**: Connected to a GPIO pin on port `GPIOA`.
- **LED_BLUE**: Connected to a GPIO pin on port `GPIOA`.
- **LED_ORANGE**: Connected to a GPIO pin on port `GPIOA`.

## How It Works
1. Task `FlashRedLedTask`:
   - Turns on the orange LED as an indicator.
   - Blinks the red LED 20 times with a 25 ms delay.
   - Turns off both the red and orange LEDs.
   - Delays for 1500 ms.

2. Task `FlashGreenLedTask`:
   - Turns on the blue LED as an indicator.
   - Blinks the green LED 160 times with a 25 ms delay.
   - Turns off both the green and blue LEDs.
   - Delays for 6000 ms.

## Dependencies
- **HAL (Hardware Abstraction Layer)**: Used for GPIO control and hardware configuration.
- **FreeRTOS**: RTOS library for multitasking.
- IDE used: STM32CubeIDE.

## Main Files
- `main.c`: Contains the main logic for hardware initialization, RTOS configuration, and task implementation.
- `stm32xxxx_hal_conf.h`: HAL Library configuration.
- `FreeRTOSConfig.h`: FreeRTOS configuration.

## How to Run
1. **Hardware Setup**:
   - Connect the LEDs according to the pins configured in `MX_GPIO_Init`.
   - Ensure the STM32 microcontroller is properly connected to the debugger/computer.

2. **Build and Flash**:
   - Open this project in STM32CubeIDE.
   - Build the project by pressing *Ctrl+B*.
   - Flash the program to the STM32 board by pressing *F11*.

3. **Monitor Output**:
   - Observe the LEDs blinking according to the patterns defined in the tasks.
