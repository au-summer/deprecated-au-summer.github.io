---
layout: page
title: Deep Learning for MINLP
description: ML-accelerated optimization for wireless networks
img:
importance: 6
category:
---

A research project applying deep learning techniques to accelerate Mixed-Integer Nonlinear Programming (MINLP) optimization problems in wireless network applications.

## Problem

MINLP problems are computationally challenging, combining the difficulties of:
- Integer programming (combinatorial explosion)
- Nonlinear programming (non-convex optimization)

Traditional solvers like Branch and Bound can be extremely slow for large-scale problems.

## Approach

Designed and implemented an **imitation learning** approach to accelerate the Branch and Bound algorithm:

- **Learning from Expert Decisions**: Train a neural network to mimic the branching decisions of an optimal solver
- **Accelerated Search**: Use the learned policy to guide the search tree exploration
- **Hybrid Strategy**: Combine learned heuristics with traditional optimization guarantees

## Application

Applied the approach to **Interference Graph Estimation** in full-duplex millimeter-wave backhaul networks:

- Network topology optimization
- Interference management in dense deployments
- Resource allocation under quality-of-service constraints

## Results

The ML-accelerated solver achieves significant speedup over traditional MINLP solvers while maintaining solution quality.
