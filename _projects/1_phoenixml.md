---
layout: page
title: PhoenixML
description: Fine-grained fault recovery for distributed GPU training
img:
importance: 1
category:
---

**PhoenixML** is a system that provides fine-grained fault recovery for distributed GPU training under transient CUDA faults. Developed at [OrderLab](https://orderlab.io/), University of Michigan, under the supervision of Prof. Ryan Huang.

## Motivation

Large-scale GPU workloads are particularly vulnerable to transient faults, including MMU errors, communication failures, and hardware glitches. Conventionally, most systems use periodic checkpointing, and upon such faults occurring, roll back the entire job. However, in many cases, only the transient execution state is affected, and most of the GPU memory contents (model parameters, optimizer states) remains intact.

## Key Insight

GPU memory can survive context failures if managed through an independent layer. Drawing on a classical OS principle of using indirection to separate resource management from execution, PhoenixML uses a **proxy context mechanism**. The lightweight proxy context maintains shared memory with the host and contains a registry that maps virtual addresses to tensor metadata.

## Technical Approach

- **Proxy Context**: When a fault occurs, PhoenixML spawns a new CUDA context and uses the proxy to remap existing GPU pages into it, allowing reconstruction of access to persistent state without data copying.

- **Runtime Interposition Layer**: Transparently monitors CUDA allocation and kernel-launch calls, managing virtual memory logic at the CUDA level to track tensor lifetimes across context boundaries.

- **Recovery Protocol**: Coordinates context respawning with the training framework through a structured recovery protocol.

## Results

For large language model training and fine-tuning workloads across multiple GPUs, PhoenixML achieves:
- **Sub-iteration recovery** (milliseconds) compared to checkpoint-based approaches (minutes)
- **Minimal work loss** with no measured overhead in steady-state operation
