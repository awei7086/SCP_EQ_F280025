# SCP_EQ_F280025

## 1. 專案概述 (Project Overview)

本專案採用TMS320F280025單晶片, 程式主要用於測試治具,提供模擬信號。
兩組pwm做出之後，經由串接一顆10K歐姆電阻及並接104電容作為濾波後產出sine wave
此二組sine wave 分別模擬Vgrid市電電壓及Igrid市電電流

Vgrid 振幅一組ADC所控制 Vamp 
Igrid 振幅一組ADC所控制 Iamp
Vgrid及Igrid頻率經由一組ADC所控制 Freq

AMP=0V    Vgrid/Igrid sine wave 振幅=0
AMP=1.65V Vgrid/Igrid sine wave 振幅=0.825~2.475
AMP=3.3V  Vgrid/Igrid sine wave 振幅=0~3.3

Freq=0V    Vgrid/Igrid sine wave 頻率=40HZ
AMP=3.3V   Vgrid/Igrid sine wave 頻率=70HZ

pin define: 
A0 ：  Vamp 
A1 ：  Iamp 
A2 ：  Freq
GPIO1 : Igrid PWM
GPIO2 : Vgrid PWM



## 2. 硬體平台 (Hardware Platform)

MCU：
TMS320F280025 (TI C2000)

系統時脈：
SYSCLK = 100 MHz

使用的周邊模組：

- ePWM
- ADC
- GPIO
- PIE Interrupt

---

## 3. 軟體架構 (Software Architecture)

系統主要流程如下：

main()
    ↓
系統初始化
    ├─ Clock 設定
    ├─ GPIO 初始化
    ├─ ADC 初始化
    └─ PWM 初始化

啟用 Interrupt 後進入控制迴路。

---

## 4. 專案結構 (Project Structure)

