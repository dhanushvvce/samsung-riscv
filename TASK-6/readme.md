# Intruder Detection using IR Sensor

## Overview
This project is part of Task 6 of the Samsung RISC-V program. The objective is to design an intruder detection system using an IR sensor, a buzzer, and an LED. When an intruder is detected, the system activates an alarm (buzzer) and visual alert (LED) to notify about unauthorized access.

![alt text](image.png)

![alt text](image-2.png)

![alt text](image-1.png)

## Components Required:

1. VSD Squadron Mini
2. IR Sensor
3. Buzzer
4. LED
5. 330 ohm Resistor
6. Jumper wires
7. Breadboard

## Pin Connections:

| **Component** | **PIN on Board** |
|--------------|------------------|
| LED         | Pin 6             |
| Buzzer      | Pin 5             |
| IR Sensor   | Pin 4             |

## Working Principle:
The IR sensor detects an object in its proximity. When an intruder is detected:
- The sensor sends a signal to the microcontroller.
- The microcontroller processes the signal and turns ON the LED and buzzer.
- The system remains in an alert state until the intruder is no longer detected.

## Code Implementation:
The program will be written in C and deployed on the VSD Squadron Mini board. It will read the sensor input and control the LED and buzzer accordingly.

#include <ch32v00x.h>
#include <debug.h>

void GPIO_Config(void)
{
GPIO_InitTypeDef GPIO_InitStructure = {0}; //structure variable GPIO_InitStructure of type GPIO_InitTypeDef which is used for GPIO configuration.

RCC_APB2PeriphClockCmd(RCC_APB2Periph_GPIOC, ENABLE); // to Enable the clock for Port C
//pin 4 OUT PIN FOR IR SENSOR
GPIO_InitStructure.GPIO_Pin = GPIO_Pin_4 ; // Defines which Pin to configure
GPIO_InitStructure.GPIO_Mode = GPIO_Mode_IPU; // Defines Input Type
GPIO_Init(GPIOC, &GPIO_InitStructure);

//Pin 5 for Buzzer
GPIO_InitStructure.GPIO_Pin = GPIO_Pin_5 ; // Defines which Pin to configure
GPIO_InitStructure.GPIO_Mode = GPIO_Mode_Out_PP; // Defines Output Type
GPIO_InitStructure.GPIO_Speed = GPIO_Speed_50MHz; // Defines speed
GPIO_Init(GPIOC, &GPIO_InitStructure);

//pin 6 IS LED PIN
GPIO_InitStructure.GPIO_Pin = GPIO_Pin_6 ; //
GPIO_InitStructure.GPIO_Mode = GPIO_Mode_Out_PP; // Defines Output Type
GPIO_InitStructure.GPIO_Speed = GPIO_Speed_50MHz; // Defines speed

GPIO_Init(GPIOC, &GPIO_InitStructure);

}


int main(void)
{
uint8_t IR = 0;
uint8_t set=1;
uint8_t reset=0;
NVIC_PriorityGroupConfig(NVIC_PriorityGroup_1);// Configuring NVIC priority group
SystemCoreClockUpdate();// Update System Core Clock
GPIO_Config();//Call GPIO configuration function

while(1)
{
    IR = GPIO_ReadInputDataBit(GPIOC, GPIO_Pin_4);
    if (IR==1)
    {
        //If IR sensor detects, then Buzzer and LED will be ON
        GPIO_WriteBit(GPIOC, GPIO_Pin_6, set);
        GPIO_WriteBit(GPIOC, GPIO_Pin_5, set);
        }
    
    else{
        //If IR sensor doesn't detect, then Buzzer and LED will be OFF
        GPIO_WriteBit(GPIOC, GPIO_Pin_6,reset);
        GPIO_WriteBit(GPIOC, GPIO_Pin_5,reset);
    }

    }
    
}

## Applications:
- Home security systems
- Automated door security
- Industrial safety systems

## Future Improvements:
- Integration with GSM module for remote alerts
- Implementation of a camera module for image capturing
- Enhancing detection range with multiple sensors
