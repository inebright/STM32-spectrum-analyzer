# STM32-spectrum-analyzer
Real-time FFT analysis using CMSIS DSP library and DMA buffers

> fft review and cmsis functions
Microphone –> ADC DMA –> CMSIS FFT –> oled display

To avoid aliasing we need to (nyquist rate) sample at twice the highest frequency we want to capture- up to 20khz, minimum of 40khz.
Using ADC on cpu is too tasking to be constantly pulling adc for new samples and also get consistent sample period.
### ADC DMA initialisation
Using CUBEMX tool to generate and HAL, only certain channels could be mapped to certain peripherals. 
For example, the ADC peripheral could only be mapped to the following: dma-2 stream 0/4
> Used DMA 2 stream 0- ADC1IN7 pin PA7
> ADC mode continuous, DMA continuous, DMA request mode circular 

### 4 pin I2C SSD1306 
displayFFT based on [4ilo/ssd1306-stm32HAL](https://github.com/4ilo/ssd1306-stm32HAL) library
- fonts.c fonts.h, ssd1306.c, ssd1306.h
- 3.3v, GND
- I2C2
- SDA PB3
- SCL PB10

### functions
> displayFFT- 
> doFFT- 

>>> INCLUDE PATH FOR CMSIS DSP
STM32CUBE PACKAGE COMES WITH CUBEIDE FOR WHEN YOU INITIALIZE TARGET
```
- COPY CMSIS/DSP/INCLUDE TO CUBE PROJECT FOLDER- DSP/INCLUDE
- COPY CMSIS/LIB TO /LIB
```

>PROJECT PROPERTIES ASSEMBLER PRE-PROCESSOR
INCLUDE PATHS-WORKSPACE UNDER DRIVERS/CMSIS
```
- MCU GCC LINKER-LIBRARIES
- INCLUDE- name of library arm_cortexM4lf-math
- SEARCH PATH-workspace driver-cmsis-lib-gcc
> PREPROCESSOR GCC COMPILER
- DEFINE SYMBOLS- ADD ARM_MATH_CM4
```
