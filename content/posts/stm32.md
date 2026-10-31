+++
date = '2026-08-13T18:42:48+08:00'
draft = false
title = 'Stm32: HOW TO READ the STM32F103 reference manual'
tags=['STM32']
categories=[]
+++

# HOW to use the STM32F103 reference manual to program 

We have 3 methods to program the stm32f103:
1. use the stm32cubeide/stm32cubemx and HAl
2. use the SPL www.st.com/en/embedded-software/stsw-stm32054.html
3. derectly write the assembly code

We can find the reference manual and the datasheet of the stm32f103 at www.st.com

[STM32F103-Reference-Manual](https://www.st.com/resource/en/reference_manual/cd00171190-stm32f10xxx-stm32f101xx-stm32f102xx-and-stm32f103xx-advanced-armbased-32bit-mcus-stmicroelectronics.pdf)
[STM32F103-Datasheet](https://www.st.com/resource/en/datasheet/stm32f103c8.pdf)


[STM32F4-Reference-Manual](https://www.st.com/resource/en/reference_manual/dm00031020-stm32f101xx-stm32f102xx-stm32f103xx-stm32f105xx-and-stm32f107xx-advanced-armbased-32bit-mcus-stmicroelectronics.pdf)
[STM32F4-Datasheet](https://www.st.com/resource/en/datasheet/stm32f407vgt6.pdf)

For example, we need to light a LED in the stm32f103.
When we look the board of the stm32,we can find that the LED is connected to the GPIO.13 pin.

Through reading '3 Memory and bus architecture' in the reference manual, we can find that the APB2 is the bus clock of the GPIOx、AFIO...

1 then we can find that the GPIOx is the APB2ENR register.

2 then we can find that the GPIO_InitTypeDef is the GPIOx_CRH register.

3 then we can find that the 9.2.4Port output data register (GPIOx_ODR) (x=A..G)
# IO
GPIO LED blinking and key input

## 1.APB2 peripheral clock enable register (RCC_APB2ENR)
RCC->APB2ENR = 0x00000010;

```c
RCC_APB2Periph_GPIOx
```


## 2.GPIO_InitTypeDef
GPIOC->CRH = 0x00300000;

```c
// SPL:initialize the GPIO_InitStruct
GPIO_InitTypeDef GPIO_InitStruct;
GPIO_InitStruct.GPIO_Pin = GPIO_Pin_13;
GPIO_InitStruct.GPIO_Mode = GPIO_Mode_Out_PP;
GPIO_InitStruct.GPIO_Speed = GPIO_Speed_50MHz;
```

how to select the mode of GPIO?
[[GPIO_Mode]]

## 3.GPIO_Init(GPIOx, &GPIO_InitStruct)

GPIOC->ODR = 0x00002000;// low voltage= light the led, 0-lightt, 1-dark

```c
GPIO_Init(GPIOx, &GPIO_InitStruct);
```
 
# other Core Peripheral Module‌
timers, interrupts, serial communication and ADC acquisition

# Communication Protocol Peripheral Module‌
UART → I2C → SPI → CAN

# System Integration
combine the learned peripherals to complete a comprehensive mini-project, such as "adjusting LED brightness via PWM controlled by keys + reporting ADC collected voltage values through serial port", to connect scattered knowledge points into complete engineering capabilities.