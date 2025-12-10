# STM32 UART LED Controller

A robust, interrupt-driven embedded application for the STM32 Nucleo board. This project implements a custom Command Line Interface (CLI) over UART to control onboard LEDs. 

It demonstrates professional embedded practices including **non-blocking UART reception**, **Timer interrupts** for precise LED blinking, and **debounced button inputs**.

## 🚀 Features

* **Custom String Parser:** specific commands (`LED1 ON`, `ALL OFF`) are parsed from a raw char buffer.
* **Non-Blocking Architecture:** * UART uses `HAL_UART_RxCpltCallback` to receive data in the background.
    * Blinking logic is handled by a Hardware Timer (TIM2), ensuring the main loop never blocks.
* **Adjustable Speed:** The Blue User Button toggles the blink frequency between **Fast (100ms)** and **Slow (500ms)**.
* **Safety:** Includes buffer overflow protection and input validation.

## 🛠 Hardware Used

* **Microcontroller:** STM32 Nucleo-144 (L552ZE-Q) *[Or update this to your specific board]*
* **Peripherals:** * **LPUART1:** For serial communication (Connected to ST-Link USB).
    * **TIM2:** For non-blocking timekeeping.
    * **GPIO:** LD1 (Green), LD2 (Blue), LD3 (Red).

## 💻 Serial Commands

Connect a terminal (PuTTY, minicom, TeraTerm) at **115200 baud**.

| Command | Description |
| :--- | :--- |
| `LED1 ON` | Turns LED 1 solid ON. |
| `LED1 OFF` | Turns LED 1 OFF. |
| `LED1 BLINK` | Starts blinking LED 1 at the current speed. |
| `LED2 ...` | Same commands available for LED 2. |
| `LED3 ...` | Same commands available for LED 3. |
| `ALL ON` | Turns all LEDs solid ON. |
| `ALL OFF` | Turns all LEDs OFF. |

## ⚙️ How to Run

1.  Open the project in **STM32CubeIDE**.
2.  Build the project (Hammer icon).
3.  Connect the Nucleo board via USB.
4.  Run/Debug to flash the code.
5.  Open a Serial Terminal (115200 / 8-N-1) and hit **Enter** to see the `Nereya>` prompt.

## 📂 Project Structure

* `Core/Src/main.c`: Main loop and command parsing logic.
* `Core/Src/stm32l5xx_it.c`: Interrupt Service Routines (ISRs).
* `Core/Inc/`: Header files and configuration.
