TARGET = dyndev
KERNEL_PATH = /lib/modules/$(shell uname -r)/build
BUILD_PATH = $(PWD)

obj-m := $(TARGET).o

all: $(TARGET).c
	@sudo make -C $(KERNEL_PATH) M=$(BUILD_PATH) modules
	
clean:
	@sudo make -C $(KERNEL_PATH) M=$(BUILD_PATH) clean
	@rm -rf .$(TARGET).ko.cmd $(TARGET).mod.c $(TARGET).mod.o $(TARGET).o $(TARGET).prelink.o .modules.order.cmd .Module.symvers.cmd $(TARGET).mod .$(TARGET).mod.cmd .$(TARGET).mod.o.cmd .$(TARGET).o.cmd .$(TARGET).prelink.o.cmd modules.order Module.symvers
	
load:
	@echo "Loading module!"
	@sudo insmod $(TARGET).ko
	
unload:
	@echo "Unloading module!"
	@sudo rmmod $(TARGET).ko
