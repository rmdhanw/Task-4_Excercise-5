# FreeRTOS LED Blinking Example on STM32

This repository contains an example program to demonstrate the use of FreeRTOS on STM32 for controlling LED blinking using two separate tasks: one for a green LED and another for a red LED. The program runs two tasks concurrently, simulating multitasking on the STM32 microcontroller.

## Description

This project demonstrates how to use FreeRTOS for multitasking on an STM32 microcontroller. Two tasks are created to blink the green and red LEDs connected to the STM32 GPIO pins. The green and red LEDs blink at different intervals, showcasing task concurrency.

## Key Features

- **FreeRTOS Tasks**: Two tasks, `GreenLedTask` and `RedLedTask`, are implemented to blink LEDs.
- **Shared Resource Access**: A flag (`startFlag`) is used to demonstrate access to shared resources between tasks.
- **GPIO Configuration**: GPIO pins are configured to control the LEDs.
- **Multitasking**: FreeRTOS scheduler manages the two tasks to run concurrently.

## LED Blinking Behavior

- **Green LED**: Flashes every 500ms.
- **Red LED**: Flashes every 100ms.

## Hardware Setup

- **Green LED**: Connected to GPIOA_PIN_0.
- **Red LED**: Connected to GPIOA_PIN_2.
- **Blue LED**: Connected to GPIOA_PIN_1 (not used in this example, but available for future tasks).

## Files

- `main.c`: Main program containing initialization, FreeRTOS tasks, and GPIO configurations.
- `cmsis_os.h`: FreeRTOS API header for STM32.
- `stm32f4xx_hal.h`: STM32 HAL header for hardware abstraction.

 ## How to Run

1. Open the project in STM32CubeIDE or STM32CubeMX.
2. Build and upload the firmware to the STM32 board.
3. After programming, you should see:
   - **Green LED** blinking every 500ms.
   - **Red LED** blinking every 100ms.

## Explanation of Key Functions

- **`SystemClock_Config()`**: Configures the system clock to use the High-Speed Internal (HSI) oscillator.
- **`MX_GPIO_Init()`**: Initializes the GPIO pins for the LEDs.
- **`GreenLedTask()`**: Task to control the green LED. It turns on the green LED, calls `accessSharedData()` to toggle the shared flag, then turns off the green LED and delays for 500ms.
- **`RedLedTask()`**: Task to control the red LED. It turns on the red LED, calls `accessSharedData()` to toggle the shared flag, then turns off the red LED and delays for 100ms.
- **`accessSharedData()`**: Function to simulate access to shared data. It toggles the value of `startFlag` and controls the state of an additional GPIO pin (not used in the LED flashing logic).

## Requirements

- **STM32 Microcontroller**: This example is designed for STM32 boards (e.g., STM32F4 series).
- **STM32CubeIDE or STM32CubeMX**: For building and programming the STM32 firmware.

 https://github.com/rmdhanw/Task-4_Excercise-5/issues/1#issue-2719159648
