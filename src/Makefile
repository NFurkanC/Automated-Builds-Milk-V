TARGET_NAME=blink
TARGET_SUFFIX=.duo
TARGET=$(TARGET_NAME)$(TARGET_SUFFIX)
BUILD_DIR= ../build

# Check Errors
ifeq (,$(TOOLCHAIN_PREFIX))
$(error TOOLCHAIN_PREFIX is not set)
endif

ifeq (,$(CFLAGS))
$(error CFLAGS is not set)
endif

ifeq (,$(LDFLAGS))
$(error LDFLAGS is not set)
endif

# Set Compiler
CC = $(TOOLCHAIN_PREFIX)gcc

# Set Flags and Libraries
LDFLAGS += -lwiringx

# Source and Object Files
SOURCE = $(wildcard *.c)
OBJS = $(patsubst %.c,$(BUILD_DIR)/%.o,$(SOURCE))

# Build Target
$(TARGET): $(OBJS)
	@mkdir -p $(BUILD_DIR)
	$(CC) $(CFLAGS) -o $@ $(OBJS) $(LDFLAGS)

$(BUILD_DIR)/%.o: %.c
	@mkdir -p $(BUILD_DIR)
	$(CC) $(CFLAGS) -o $(BUILD_DIR)/$@ -c $<
	@rm -rf $(BUILD_DIR)/*.o

.PHONY: clean
clean:
	@rm -rf $(BUILD_DIR)
