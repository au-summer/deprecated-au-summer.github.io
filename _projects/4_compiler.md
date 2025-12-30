---
layout: page
title: Dynamic Typed Compiler
description: Rust compiler for a dynamically typed language on x86-64
img:
importance: 4
category:
---

A compiler implementation for a simple programming language supporting dynamic typing and heap allocation, targeting the x86-64 architecture.

## Implementation

Built entirely in **Rust**, the compiler includes:

### Frontend
- Lexical analysis and parsing
- Type checking for a dynamically typed language
- Semantic analysis

### Middle-end
- **Single Static Assignment (SSA)** form transformation
- Intermediate representation optimization

### Backend
- Code generation following **System V ABI**
- x86-64 assembly output
- Runtime support for dynamic typing and heap allocation

## Optimizations

- **Register Allocation**: Efficient mapping of virtual registers to physical registers
- **Assertion Removal**: Dead code elimination for runtime type checks

## Features

- Dynamic typing with runtime type checking
- Heap allocation and garbage collection support
- Standard control flow constructs
- Function definitions and calls
