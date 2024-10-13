# Custom Operating System

This project is a simple custom operating system that prints "Hello World from My Operating System" to the screen. It is built using a custom kernel written in C++, an assembly bootloader, and is packaged into a bootable ISO using GRUB.

## Project Structure

```plaintext
root/
├── build/                  # Compiled binary files
│   ├── mykernel.bin         # Kernel binary
│   ├── mykernel.iso         # Bootable ISO
├── src/                    # Source code for the OS
│   ├── kernel.cpp           # Main kernel code
│   ├── loader.s             # Assembly code for the loader
├── obj/                    # Object files
│   ├── kernel.o             # Kernel object file
│   ├── loader.o             # Loader object file
├── linker.ld               # Linker script
├── Makefile                # Makefile to automate the build process
├── README.md               # Project overview and instructions
└── LICENSE                 # License file (Apache 2.0)
```

## Requirements

Before you begin, you need the following tools installed on your system:

- `gcc` (with 32-bit support)
- `as` (GNU assembler for assembling 32-bit code)
- `ld` (GNU linker for linking 32-bit object files)
- `grub-mkrescue` (for generating a bootable ISO)
- `VirtualBox` (for testing the OS)

## Build and Run Instructions

### 1. Building the OS

To build the kernel and generate the bootable ISO image:

```bash
make mykernel.iso
```

This will compile the C++ and assembly code, link the objects, and package them into an ISO image.

### 2. Installing the Kernel

To copy the kernel binary to the `/boot` directory (requires superuser privileges):

```bash
make install
```

### 3. Running the OS in VirtualBox

You can use VirtualBox to run the custom operating system. Ensure that a virtual machine called "My Operating System" is set up, and run:

```bash
make run
```

This will start the virtual machine and boot your custom OS.

## Files

- `kernel.cpp`: The main kernel file written in C++. It defines a simple `printf` function to output to the screen and prints a message from `kernelMain`.
- `loader.s`: The assembly code for the bootloader, which prepares the system and jumps to the kernel.
- `Makefile`: Automates the build process, including compiling, linking, and generating the bootable ISO.
- `linker.ld`: The linker script to define the memory layout for the kernel.
- `mykernel.bin`: The compiled kernel binary.
- `mykernel.iso`: The bootable ISO that can be run in VirtualBox or any other virtual machine.

## Kernel Overview

The kernel is a simple C++ program that:

1. Implements a basic `printf` function to write text to the video memory at address `0xb8000` (standard text mode video memory location).
2. Contains the `kernelMain` function, which is the entry point for the operating system. It simply prints "Hello World from My Operating System" and enters an infinite loop.

## License

This project is licensed under the Apache License, Version 2.0 