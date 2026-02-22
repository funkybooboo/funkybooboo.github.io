---
layout: page
title: NateOS - Custom Operating System
permalink: /projects/nateos/
repo_url: https://github.com/funkybooboo/nateos
description: A self-built monolithic operating system written in Assembly and C.
---

**Repository:** [github.com/funkybooboo/nateos](https://github.com/funkybooboo/nateos)

A self-built monolithic operating system developed from scratch to understand low-level systems programming and OS architecture.

## Key Features

*   **Bootloader:** Custom bootloader written in x86 Assembly
*   **Kernel:** Monolithic kernel architecture
*   **Memory Management:** Custom memory allocator and paging system
*   **Process Management:** Basic process scheduling and context switching
*   **Hardware Interaction:** Direct hardware control and interrupt handling

## Technology Stack

*   **Languages:** x86 Assembly, C
*   **Architecture:** x86 (32-bit)
*   **Build Tools:** NASM assembler, GCC, custom linker scripts
*   **Testing:** QEMU for virtualized testing and debugging

## Implementation Details

*   **Boot Process:** BIOS boot, stage-1 and stage-2 bootloader
*   **Protected Mode:** Transition from real mode to protected mode
*   **GDT/IDT:** Global Descriptor Table and Interrupt Descriptor Table setup
*   **Interrupt Handling:** Hardware and software interrupt management
*   **VGA Text Mode:** Basic text output for debugging and user interaction

## Learning Outcomes

This project provides hands-on experience with:
*   Low-level hardware programming and BIOS interaction
*   Memory segmentation and paging mechanisms
*   Interrupt handling and system calls
*   Assembly language and systems architecture
*   Operating system design principles
