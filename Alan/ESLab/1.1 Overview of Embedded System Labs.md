
* Embedded System are **computer systems** that has **build in MCU or MPU.** (電腦以外的應用)
* STM32L4
	* Arm **Cortex-M4**
	* Quad-SPI Flash memory
* **Quad-SPI** (qspi)：一種進階的SPI接口，理論上速度可達SPI四倍
	* 六條線：CLK / CS / **IO0(SO) / IO1(SI) / IO2 / IO3 (雙向傳輸)**
	* 一次傳4個bit，理論上達SPI四倍速度 (SPI為單向)
* NVIDIA Jetson Nano: Cortex-A
* Raspberry Pi: Cortex-A