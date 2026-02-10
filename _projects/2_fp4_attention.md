---
layout: page
title: FP4 Attention Kernel
description: Porting SageAttention3's FP4 attention from SM120 (B300) to SM100 (B200)
img:
importance: 2
category: LLM Infrastructure
---

Porting SageAttention3's FP4 attention kernel from SM120 (B300) to SM100 (B200), with integration into TensorRT-LLM's FP4 KV Cache for zero-dequantize inference.

## Key Finding

After thorough git history analysis of SageAttention3, we discovered that the "SM100 support" that was reverted in December 2024 consisted **only of `setup.py` compilation flag changes**. The actual kernel code (`cute_extension.h`, `kernel_traits.h`) has always been SM120-only.

This means we need to **create** SM100 kernel code from scratch, not recover it.

## Technical Challenges

- **Architecture Differences**: SM100 (B200) vs SM120 (B300) have different tensor core capabilities
- **FP4 Support**: Implementing efficient FP4 quantization for attention computation
- **TensorRT-LLM Integration**: Seamless integration with existing FP4 KV Cache infrastructure

## Goals

1. Port FP4 attention to NVIDIA B200 (SM100)
2. Integrate with TensorRT-LLM's FP4 KV Cache
3. Achieve zero-dequantize inference for maximum efficiency
