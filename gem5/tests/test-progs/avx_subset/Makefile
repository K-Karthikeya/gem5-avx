# Simple Makefile to build AVX subset test
# Targets:
#   make            -> build avx_subset_test
#   make run        -> run executable
#   make clean      -> remove artifacts

CC ?= gcc
CFLAGS ?= -O2 -mavx -Wall -Wextra
LDFLAGS ?= -mavx

SRC_ASM := avx_subset.S
SRC_C   := harness.c
OBJ     := $(SRC_ASM:.S=.o) $(SRC_C:.c=.o)
BIN     := avx_subset_test

.PHONY: all run clean

all: $(BIN)

$(BIN): $(OBJ)
	$(CC) $(LDFLAGS) -o $@ $^

%.o: %.S
	$(CC) $(CFLAGS) -c -o $@ $<

%.o: %.c
	$(CC) $(CFLAGS) -c -o $@ $<

run: $(BIN)
	./$(BIN)

clean:
	rm -f $(OBJ) $(BIN)
