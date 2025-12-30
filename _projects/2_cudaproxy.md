---
layout: page
title: CudaProxy
description: Adaptive execution runtime for ML inference
img:
importance: 2
category:
---

**CudaProxy** is a CUDA runtime proxy for machine learning inference that uses CUDA Graphs and Persistent Kernels for accelerated performance without brittle kernel fusion.

## Motivation

Modern machine learning inference, particularly with Mixture-of-Experts (MoE) models, involves many small operations (routing, packing, and scattering) that incur significant kernel launch overhead, which dominates latency. The common practice is kernel fusion, which manually combines these operations into specialized kernels. However, fusion is brittle at the infrastructure level -- even minor changes in workload require re-authoring and re-tuning.

## Key Insight

This brittleness is a systems design problem: a failure to separate policy from mechanism. Model serving workloads can be naturally decomposed into two classes:
- **Static operations**: Predictable control flow and stable shapes
- **Dynamic operations**: Execution depends on actual input data

## Technical Approach

Rather than hard-coding execution strategy into kernels, CudaProxy separates the policy for dispatching kernels from the underlying mechanisms that execute them:

- **CUDA Graphs**: Static regions are captured and replayed as CUDA Graphs
- **Persistent Workers**: Dynamic regions are executed by GPU-resident persistent workers that consume tasks from a device-side queue
- **Automatic Routing**: Each request is mapped into an execution plan, and CudaProxy routes segments to the appropriate backend

Additional optimizations include:
- **Bucketing**: Group similar workloads together
- **Automatic Padding**: Handle variable-length inputs efficiently
- **Static Memory Pooling**: Minimize allocation overhead for dynamic workloads

## Results

On a series of MoE inference workloads:
- Reduces tail latency by **over 30%** compared to unfused baselines
- Approaches throughput **within 10%** of hand-tuned fusion
