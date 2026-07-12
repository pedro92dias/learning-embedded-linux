# Makefile to build the hello app

CC = gcc
CFLAGS = -Wall -g
LD = gcc
RM = rm -f

all: clean app

hello.o: hello.c helper.h
	@echo "Building hello..."
	@$(CC) -c hello.c $(CFLAGS) -o $@

helper.o: helper.c helper.h
	@echo "Building helper..."
	@$(CC) -c helper.c $(CFLAGS) -o $@

app: hello.o helper.o
	@echo "Building app..."
	@$(LD) -o $@ $^
	@$(RM) hello.o helper.o
	@echo "Build complete!"

clean:
	@echo "Cleaning up..."
	@$(RM) app hello.o helper.o
	@echo "All clean!"