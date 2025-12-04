# Smart Home Automation using STM32F401

This project is an STM32 microcontroller program that initializes and configures various **GPIO pins, ADC, and USART** to monitor sensors (PIR, Ultrasonic, LDR) and communicate with an external device via Bluetooth.  
The system starts only when **PA6** is pressed, triggering an external interrupt.

---

## 🧩 Key Components

### 🔹 GPIO Configuration
- Configures pins for sensors and LEDs.

### 🔹 ADC Initialization
- Sets up an ADC channel to read data from the **LDR sensor** (PA1).

### 🔹 USART Initialization
- Configures **USART2** for serial communication at 9600 baud.

### 🔹 Interrupt Handling
- External interrupt on **PA6** starts the system.

### 🔹 Sensor Reading & LED Control
The main loop continuously:
- Reads sensor values  
- Controls LEDs based on sensor conditions

---

## ⚙️ System Functionality

The program waits for a signal on **PA6** (interrupt-based).  
Once triggered, it monitors the following sensors:

### 🔸 **PIR Sensor (PA11)**
- Detects motion  
- Turns ON **LED at PA10**

### 🔸 **Ultrasonic Sensor**
- Trigger: **PA4**  
- Echo: **PA5**  
- Detects presence  
- Controls **LED at PA7**

### 🔸 **LDR Sensor (PA1 via ADC)**
- Reads light intensity  
- Turns ON **LED at PA8** when below threshold

### 🔸 **Bluetooth Control via USART2**
- `'1'` → Turn ON **LED at PB10**  
- `'0'` → Turn OFF **LED at PB10**

---

## 🏠 STM32 Sensor Monitoring and Home Control System

A microcontroller-based automation system using STM32F4 series that:
- Reads PIR, Ultrasonic, LDR sensors  
- Controls LEDs based on sensor state  
- Communicates over USART2 for Bluetooth operations  
- Uses **PA6** external interrupt to start monitoring system

---

## 🔌 Components & Pin Configuration

| Component | Pin | Description |
|----------|-----|-------------|
| Start Button | PA6 | Interrupt trigger |
| PIR Sensor | PA11 | Motion detection |
| PIR LED | PA10 | Motion indicator |
| Ultrasonic Trigger | PA4 | Trigger pulse |
| Ultrasonic Echo | PA5 | Echo signal |
| Ultrasonic LED | PA7 | Presence indicator |
| LDR Sensor | PA1 (ADC) | Light sensing |
| LDR LED | PA8 | Light indicator |
| Bluetooth LED | PB10 | Controlled via USART2 |
| USART2 TX | PA2 | Transmit |
| USART2 RX | PA3 | Receive |

---

## 🛠️ Project Setup Instructions

### 1️⃣ Create Project in Keil uVision5
- Open Keil 5 → Create New Project
- Select **STM32F4xx series** MCU

### 2️⃣ Configure Run-Time Environment
Enable:
- **Device → STM32Cube HAL**
- **CMSIS → Core**
- **Device → Startup**
  - Add `system_stm32f4xx.c`

### 3️⃣ Add Source Files
- Add `.c` file to the project
- Include headers:
  ```c
  #include "stm32f4xx.h"
  #include "system_stm32f4xx.h"
