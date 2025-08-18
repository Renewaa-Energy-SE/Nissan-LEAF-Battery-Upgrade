#
#             LUFA Library
#     Copyright (C) Dean Camera, 2014.
#
#  dean [at] fourwalledcubicle [dot] com
#           www.lufa-lib.org
#
# --------------------------------------
#         LUFA Project Makefile.
# --------------------------------------

MCU          = atxmega32c4
ARCH         = XMEGA
BOARD        = NONE
F_CPU        = 32000000
F_USB        = 48000000
OPTIMIZATION = 1
TARGET       = can-bridge-firmware

SRC          = \
	can-bridge-firmware.c \
	Descriptors.c \
	helper_functions.c \
	mcp25xx.c \
	sp_driver.S \
	LUFA/Drivers/USB/Class/Device/CDCClassDevice.c \
	LUFA/Drivers/USB/Core/ConfigDescriptors.c \
	LUFA/Drivers/USB/Core/DeviceStandardReq.c \
	LUFA/Drivers/USB/Core/Events.c \
	LUFA/Drivers/USB/Core/USBTask.c \
	LUFA/Drivers/USB/Core/XMEGA/Device_XMEGA.c \
	LUFA/Drivers/USB/Core/XMEGA/EndpointStream_XMEGA.c \
	LUFA/Drivers/USB/Core/XMEGA/Endpoint_XMEGA.c \
	LUFA/Drivers/USB/Core/XMEGA/Host_XMEGA.c \
	LUFA/Drivers/USB/Core/XMEGA/PipeStream_XMEGA.c \
	LUFA/Drivers/USB/Core/XMEGA/Pipe_XMEGA.c \
	LUFA/Drivers/USB/Core/XMEGA/USBController_XMEGA.c \
	LUFA/Drivers/USB/Core/XMEGA/USBInterrupt_XMEGA.c

LUFA_PATH    = LUFA
CC_FLAGS     = -DUSE_LUFA_CONFIG_HEADER -I. -std=gnu99 -fms-extensions
LD_FLAGS     = -Wl,-lm

# Default target
all:

# Include LUFA build script makefiles
include $(LUFA_PATH)/Build/lufa_core.mk
include $(LUFA_PATH)/Build/lufa_sources.mk
include $(LUFA_PATH)/Build/lufa_build.mk
include $(LUFA_PATH)/Build/lufa_cppcheck.mk
include $(LUFA_PATH)/Build/lufa_doxygen.mk
include $(LUFA_PATH)/Build/lufa_dfu.mk
include $(LUFA_PATH)/Build/lufa_hid.mk
include $(LUFA_PATH)/Build/lufa_avrdude.mk
include $(LUFA_PATH)/Build/lufa_atprogram.mk
