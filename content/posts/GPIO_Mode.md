+++
date = '2026-08-29T17:06:18+08:00'
draft = true
title = 'GPIO_Mode'
tags=["STM32F103","GPIO"]
categories=[]
+++

The GPIO mode is a set of configurations for a GPIO pin.

MCU，such as STM32,ESP32,GD32,etc.

SoC,BCM2711:4 modes,input,output,alternate function,analog input

I will explain the GPIO mode of STM32F103 in detail.

# STM32F103
There are 8 modes for the GPIO pin.

1. Input Modes


Mode|Description|Scene
---|---|---
GPIO_Mode_IN_FLOATING|浮空输入Floating input|I2C,USART_RX
GPIO_Mode_IPU|上拉输入Pull-up input|Button detection (high when not pressed)
GPIO_Mode_IPD|下拉输入Pull-down input|Needs low default signal from outside
GPIO_Mode_AIN|模拟输入Analog input|ADC sampling,comparator input



2. Output Modes

Mode|Description|Scene
---|---|---
GPIO_Mode_Out_OD|开漏输出,只能输出低电平（高阻态需外接上拉）|I2C总线、电平匹配。
GPIO_Mode_Out_PP|推挽输出,可输出高/低电平，驱动能力强|LED、USART_TX、SPI


3. 复用功能模式 (Alternate Function Modes)

· 复用开漏输出 (GPIO_Mode_AF_OD)
  引脚由外设控制（如I2C），需外接上拉。
· 复用推挽输出 (GPIO_Mode_AF_PP)
  引脚由外设控制（如USART、SPI），无需外接上拉。


---

速记口诀（中英对照）

浮空上拉下（输入三态），模拟单独采（ADC）。
开漏推挽出（输出），复用归外设（AF）。

# STM32F4

