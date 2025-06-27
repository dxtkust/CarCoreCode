# CarCoreCode

本项目为基于 STM32F1 系列单片机的小车核心控制代码，包含 GPIO、定时器、串口等外设的初始化与控制，实现了小车的基本运动、循迹和串口遥控功能。

## 目录结构

```
CarCoreCode/
├── Inc/         # 头文件
│   ├── gpio.h
│   ├── main.h
│   ├── stm32f1xx_hal_conf.h
│   ├── stm32f1xx_it.h
│   ├── tim.h
│   └── usart.h
└── Src/         # 源文件
    ├── gpio.c
    ├── main.c
    ├── stm32f1xx_hal_msp.c
    ├── stm32f1xx_it.c
    ├── system_stm32f1xx.c
    ├── tim.c
    └── usart.c
```

## 功能简介

- **小车运动控制**：支持前进、后退、左转、右转、停止等动作。
- **循迹模式**：通过 GPIO 读取循迹传感器，实现自动循迹。
- **串口遥控**：通过 USART2 接收指令，支持模式切换与动作控制。

## 快速开始

1. 使用 STM32CubeMX 或 Keil/IAR 打开工程，选择对应的芯片型号（如 STM32F103C8T6）。
2. 编译并下载程序到开发板。
3. 通过串口助手发送如下指令控制小车（默认波特率 9600）：
   - `F`：前进
   - `B`：后退
   - `L`：左转
   - `R`：右转
   - `S`：停止
   - `M`：切换循迹/遥控模式

## 主要文件说明

- [`main.c`](CarCoreCode/Src/main.c)：主程序入口，包含小车运动、循迹、串口回调等核心逻辑。
- [`gpio.c`](CarCoreCode/Src/gpio.c)：GPIO 初始化与配置。
- [`tim.c`](CarCoreCode/Src/tim.c)：定时器（PWM）初始化与配置。
- [`usart.c`](CarCoreCode/Src/usart.c)：串口初始化与配置。
- [`stm32f1xx_it.c`](CarCoreCode/Src/stm32f1xx_it.c)：中断服务函数。

## 硬件连接说明

- 电机驱动控制：PB12~PB15
- PWM 输出：PB8（TIM4_CH3）、PB9（TIM4_CH4）
- 循迹传感器输入：PA4、PA5、PB1
- 串口通信：USART2（PA2/PA3）

## 版权声明

Copyright (c) 2025 STMicroelectronics.

本项目代码仅供学习与交流，禁止用于商业用途。
