---
layout: page
title: tiny-trtllm
description: Minimal C++ implementation of TensorRT-LLM's core architecture (~3,000 lines)
img:
importance: 1
category: LLM Infrastructure
---

A minimal, educational implementation of [TensorRT-LLM](https://github.com/NVIDIA/TensorRT-LLM)'s core architecture in ~3,000 lines of C++.

## Focus

**System-level C++ runtime, not CUDA kernels.** All computation uses TensorRT built-in layers and cuBLAS. The project demonstrates how TensorRT-LLM's serving infrastructure works:

- **Paged KV Cache** - Memory-efficient key-value cache management
- **Inflight Batching** - Dynamic batching for optimal GPU utilization
- **TensorRT Plugin Mechanism** - Custom operator integration
- **C++ Runtime** - The infrastructure that ties it all together

## Architecture

```
┌─────────────────────────────────────────────────┐
│                  Python API                      │
│              (TinyLLM class)                     │
├─────────────────────────────────────────────────┤
│               pybind11 bindings                  │
├──────────┬──────────┬──────────┬────────────────┤
│ Engine   │ KV Cache │Scheduler │   Builder      │
│ Runtime  │ Manager  │(Inflight │  (Network +    │
│(TRT exec)│ (Paged)  │ Batching)│   Weights)     │
├──────────┴──────────┴──────────┴────────────────┤
│            TensorRT Engine + Plugins             │
└─────────────────────────────────────────────────┘
```

## Why This Project

Understanding production LLM serving systems requires diving into complex codebases. This project distills the essential concepts into readable, well-documented code that serves as a learning resource for anyone interested in LLM infrastructure.
