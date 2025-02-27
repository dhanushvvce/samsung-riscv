
# **IR Sensor-Based Hurdle Detection with LED Alert (RISC-V Board)**  

## **Project Overview**  
This project demonstrates **hurdle detection** using an **Infrared (IR) sensor** interfaced with a **RISC-V development board**. The system continuously monitors for obstacles, and when one is detected, an **LED indicator lights up** or blinks as an alert. This setup is useful for applications such as **autonomous robots, security systems, and smart automation**.  

---

## **Hardware Components**  
To build this project, you will need:  
- **RISC-V Development Board** 
- **IR Proximity Sensor**  
- **LED** (for visual indication)  
- **Resistor (330Ω)** (for LED current limiting)  
- **Connecting jumper Wires**  
- **Breadboard** 

---

## **How It Works**  
1. The **IR sensor** emits infrared light and detects reflections from nearby objects.  
2. If an object is detected, the **IR sensor outputs a LOW signal**; otherwise, it remains HIGH.  
3. The **RISC-V board reads the sensor signal** and processes the data.  
4. If an obstacle is detected, the **LED turns ON or blinks**, providing a visual alert.  
5. The system continuously checks for obstacles in a loop.  

---

## **Circuit Connections**  
| Component         | Pin Connection (RISC-V Board) |
|------------------|-----------------------------|
| **IR Sensor VCC**  | **3.3V / 5V**                               |
| **IR Sensor OUT**  | **GPIO (GPIO5)**      |
| **LED Anode (+)**  | **GPIO (GPIO6)**     |
| **LED Cathode (-)**| **GND**                     |


```c
#include <ch32v00x.h>
#include <debug.h>

void GPIO_Config(void) {
    GPIO_InitTypeDef GPIO_InitStructure = {0};
    RCC_APB2PeriphClockCmd(RCC_APB2Periph_GPIOD, ENABLE);
    
    GPIO_InitStructure.GPIO_Pin = GPIO_Pin_4;
    GPIO_InitStructure.GPIO_Mode = GPIO_Mode_IPU;
    GPIO_Init(GPIOD, &GPIO_InitStructure);
    
    GPIO_InitStructure.GPIO_Pin = GPIO_Pin_6;
    GPIO_InitStructure.GPIO_Mode = GPIO_Mode_Out_PP;
    GPIO_InitStructure.GPIO_Speed = GPIO_Speed_50MHz;
    GPIO_Init(GPIOD, &GPIO_InitStructure);
}

int main(void) {
    uint8_t IR = 0;
    uint8_t set = 1;
    uint8_t reset = 0;
    
    NVIC_PriorityGroupConfig(NVIC_PriorityGroup_1);
    SystemCoreClockUpdate();
    Delay_Init();
    GPIO_Config();
    
    while(1) {
        IR = GPIO_ReadInputDataBit(GPIOD, GPIO_Pin_4);
        if (IR == 1) {
            GPIO_WriteBit(GPIOD, GPIO_Pin_6, reset);
        } else {
            GPIO_WriteBit(GPIOD, GPIO_Pin_6, set);
        }
        Delay_Ms(100);
    }
}
```



---

