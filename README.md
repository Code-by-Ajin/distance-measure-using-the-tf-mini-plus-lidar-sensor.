# distance-measure-using-the-tf-mini-plus-lidar-sensor.


# STM32H723ZG + TFmini Plus LiDAR Interface

This repository provides a robust, non-blocking C++ implementation for reading distance, signal strength, and temperature data from a TFmini Plus LiDAR sensor using an STM32H723ZG Nucleo board. 

Built using the **Arduino Framework** on **PlatformIO**, this code utilizes hardware UART and strict checksum validation to ensure high-speed, accurate readings without stalling the main processor loop.

---

## 📋 1. Prerequisites

Before starting, ensure you have the following:
* **Hardware:** ST Nucleo H723ZG board, TFmini Plus LiDAR sensor, and jumper wires.
* **Software:** [Visual Studio Code](https://code.visualstudio.com/) installed on your computer.

---

## 🔌 2. Hardware Wiring Procedure

The TFmini Plus requires a 5V power supply, but its data lines safely operate at a 3.3V logic level, allowing direct connection to the STM32's GPIO pins. 

**Wire your sensor before plugging the board into your computer:**

| TFmini Plus Wire | Function | STM32H723ZG Pin | Notes |
| :--- | :--- | :--- | :--- |
| **Red** | 5V Power | **5V** | Do not connect to 3.3V |
| **Black** | Ground | **GND** | Connects to any ground pin |
| **Green** | TX (Transmit) | **PA10** (UART1 RX) | Sensor TX connects to Board RX |
| **White** | RX (Receive) | **PA9** (UART1 TX) | Sensor RX connects to Board TX |

---

## 💻 3. PlatformIO Installation

This project relies on PlatformIO to manage the STM32 toolchains and Arduino framework.

1. Open **Visual Studio Code**.
2. Navigate to the **Extensions** view (`Ctrl+Shift+X` or `Cmd+Shift+X`).
3. Search for **PlatformIO IDE** and click **Install**.
4. Restart VS Code once the installation finishes. You should now see an alien head icon on the left sidebar.

---

## 🚀 4. Creating the Project & Adding Code

If you are cloning this repository directly:
```bash
git clone [https://github.com/Code-by-Ajin/your-repo-name.git](https://github.com/Code-by-Ajin/your-repo-name.git)

### 🚀 Creating the Project from Scratch

If you are building this project from scratch, follow these steps:

1. Click the **PlatformIO icon** (alien head) on the left sidebar.
2. Click **PIO Home > Open**.
3. Click **+ New Project** and configure it:
   * **Name:** `TFmini_STM32`
   * **Board:** ST Nucleo H723ZG
   * **Framework:** Arduino
4. Click **Finish**.

### 📂 Configuring the Correct Areas

#### 1. `platformio.ini` (Root Directory)
Open `platformio.ini` and ensure your environment is set up for the correct baud rate:

```ini
[env:nucleo_h723zg]
platform = ststm32
board = nucleo_h723zg
framework = arduino
monitor_speed = 115200
```

#### 2. `main.cpp` (`src/` Directory)
Navigate to the `src/` folder, open `main.cpp`, and paste the provided sensor logic code here. This file contains the `setup()` and `loop()` functions that read and parse the UART data.

---

### ⚡ 5. Building and Uploading

1. Connect your **STM32H723ZG Nucleo** to your computer via USB.
2. Locate the **PlatformIO Toolbar** at the very bottom of the VS Code window (the blue ribbon).
3. **Build:** Click the checkmark icon (`✓`) to compile the project.
4. **Upload:** Click the right-pointing arrow icon (`→`) to flash the code to the STM32.
5. **Monitor:** Click the plug icon (`🔌`) to open the Serial Monitor.

#### 📋 Expected Output
If wired and uploaded correctly, your terminal will display:

```text
STM32H723ZG + TFmini Plus Initialized!
Waiting for data...
Distance: 120 cm    Strength: 4500      Temp: 24.5 °C
Distance: 121 cm    Strength: 4510      Temp: 24.5 °C
```
