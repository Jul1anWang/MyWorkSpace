# Outline

1. Side-channel experiment
2. Development
3. Writing
4. Plan





# Side-channel experiment

## ChipWhisperer Level 2 Starter Kit

### Hardware

I have a CW suite to run crypto code and capture power traces. It comes from https://rtfm.newae.com/ with a Capture borad Chipwhisperer-Lite and a CW-308T UFO board which is mother board for mcu, in this suite, it contains 3 mcu as target board, which are 8-bit XMEGA, 32-bit STM32F071(Cortext-M0) and STM32F303(Cortex-M4)

![](https://rtfm.newae.com/Starter%20Kits/Images/lvl2-starter.jpg)

The rest of this suite haven't served for me until now.

### Software

Newae offers a python package **chipwhisperer**, which can be installed from pypi. The package offers basic function about communication and trace capture. Demos and courses of side-channel evaluation on Chipwhisperer are offered by a jupyter notebook. How to use the demos and the package can be seen in  [ChipWhisperer — ChipWhisperer 5.5.0 documentation](https://chipwhisperer.readthedocs.io/en/latest/)。In addition,  newae offers basic communication for target board, the arm part is punctuate from  https://github.com/STMicroelectronics/STM32CubeF3/tree/master/Drivers/STM32F3xx_HAL_Driver; The interface between board and chipwhisperer is offered two, implementation is in "victims/firmware/simpleserial" and demos are in "victims/firmware/"



Now I used a simplified library learned from https://github.com/KULeuven-COSIC/Masked-Comparison/tree/main/jupyter, that likes a virtual environment for each experiment like venv in python. Structure is listed as follows:

- crypto/**Makefile.crypto** :

- hal/ : contains Makfile.hal and stm32f3xx hal library
- simpleserial/ : contains interface for  communication
- src/: core code of schems under test and a base simpleserialxxxx.c and a makefile
- ...: like a python 📂 contains scripts of capturing and analyzing

In PC, we compiled this 📂 with arm-none-eabi-gcc, when we use windows, we use  [The xPack GNU Arm Embedded GCC](https://xpack.github.io/arm-none-eabi-gcc/), similarly, we use xpack opanocd and xpack gdb from [**The xPack Project**](https://xpack.github.io/). In a specific case, we use QEMU from xpack to simulate ARM-Cortex-M.

## Other side-channel tools

### Lecroy HDO6032A

### Sasebo-W

