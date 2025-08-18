#
# Makefile for the CANBRIDGE-2port project
#

# Target firmware name
TARGET = can-bridge-firmware

# MCU settings
MCU = stm32f105rc
CPU = cortex-m3
F_CPU = 25000000

# Build directory
BUILD_DIR = build

# Compiler and linker
CC = arm-none-eabi-gcc
AS = arm-none-eabi-as
LD = arm-none-eabi-gcc
OBJCOPY = arm-none-eabi-objcopy
SIZE = arm-none-eabi-size

# Source files and paths
VPATH = Src Drivers/STM32F1xx_HAL_Driver/Src MDK-ARM

C_SOURCES = \
  can-bridge-firmware.c \
  main.c \
  gpio.c \
  can.c \
  iwdg.c \
  stm32f1xx_it.c \
  stm32f1xx_hal_msp.c \
  system_stm32f1xx.c \
  stm32f1xx_hal_gpio_ex.c \
  stm32f1xx_hal_can.c \
  stm32f1xx_hal.c \
  stm32f1xx_hal_rcc.c \
  stm32f1xx_hal_rcc_ex.c \
  stm32f1xx_hal_gpio.c \
  stm32f1xx_hal_dma.c \
  stm32f1xx_hal_cortex.c \
  stm32f1xx_hal_pwr.c \
  stm32f1xx_hal_flash.c \
  stm32f1xx_hal_flash_ex.c \
  stm32f1xx_hal_exti.c \
  stm32f1xx_hal_iwdg.c \
  stm32f1xx_hal_tim.c \
  stm32f1xx_hal_tim_ex.c

S_SOURCES = \
  startup_stm32f105xc.s

# Compiler flags
CFLAGS = -mcpu=cortex-m3 -mthumb -Wall -g -O2
CFLAGS += -DUSE_HAL_DRIVER -DSTM32F105xC

# Include paths
INCLUDES = \
  -IInc \
  -IDrivers/STM32F1xx_HAL_Driver/Inc \
  -IDrivers/STM32F1xx_HAL_Driver/Inc/Legacy \
  -IDrivers/CMSIS/Device/ST/STM32F1xx/Include \
  -IDrivers/CMSIS/Include

# Linker script and flags
LDFLAGS = -mcpu=cortex-m3 -mthumb -Wl,-Map=$(BUILD_DIR)/$(TARGET).map,--cref -Wl,--gc-sections

# Object files
OBJECTS = $(addprefix $(BUILD_DIR)/,$(C_SOURCES:.c=.o))
OBJECTS += $(addprefix $(BUILD_DIR)/,$(S_SOURCES:.s=.o))

all: $(BUILD_DIR)/$(TARGET).hex

$(BUILD_DIR)/%.o: %.c
	@mkdir -p $(dir $@)
	$(CC) -c $(CFLAGS) $(INCLUDES) $< -o $@

$(BUILD_DIR)/%.o: %.s
	@mkdir -p $(dir $@)
	$(CC) -c $(CFLAGS) $(INCLUDES) $< -o $@

$(BUILD_DIR)/$(TARGET).elf: $(OBJECTS)
	$(LD) $(CFLAGS) $(INCLUDES) -o $@ $(OBJECTS) $(LDFLAGS)

$(BUILD_DIR)/$(TARGET).hex: $(BUILD_DIR)/$(TARGET).elf
	$(OBJCOPY) -O ihex $< $@

clean:
	rm -rf $(BUILD_DIR)

.PHONY: all clean
