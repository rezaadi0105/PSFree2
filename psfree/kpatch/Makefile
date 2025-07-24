TARGET_VERSIONS = 700 750 800 850 900 903 950

CC = gcc
OBJCOPY = objcopy
CFLAGS = -O3 -std=gnu11 -Wno-int-conversion -masm=intel -nostartfiles -fcf-protection=none -Tscript.ld

.PHONY: all
ALL_SOURCES = $(TARGET_VERSIONS:%=%.c)
ALL_OBJECTS = $(TARGET_VERSIONS:%=%.o)
ALL_ELF = $(TARGET_VERSIONS:%=%.elf)

all: $(ALL_BINS)

%.bin: %.o
	$(CC) $< -o $*.elf $(CFLAGS)
	$(OBJCOPY) -O binary --only-section=.text $*.elf $@
	-rm -f $*.bin

.PHONY: clean
clean:
	-rm -f $(ALL_OBJECTS) $(ALL_ELF)
