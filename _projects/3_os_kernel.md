---
layout: page
title: OS Kernel Implementation
description: Thread library and virtual memory pager on UNIX-like systems
img:
importance: 3
category:
---

A comprehensive operating system kernel implementation project completed as part of EECS 482 at the University of Michigan.

## Components

### Thread Library
Developed a C++ thread library implementing:
- **Synchronization Primitives**: Mutexes and condition variables using UNIX context management techniques
- **Thread Lifecycle Management**: Creation, scheduling, and destruction
- **Context Switching**: Efficient CPU state preservation and restoration
- **CPU Booting**: Multi-processor initialization

### Virtual Memory Pager
Implemented a virtual memory system with:
- **Page Fault Handling**: On-demand paging with efficient fault resolution
- **Process Management**: Creation, forking, and destruction
- **Copy-on-Write (CoW)**: Memory optimization for forked processes
- **Page Sharing**: Efficient memory utilization across processes

## Technical Highlights

- Implemented on UNIX-like systems using low-level system calls
- Focus on correctness and performance optimization
- Extensive testing under various workload conditions
