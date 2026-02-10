---
layout: page
title: MCPSec
description: Formal verification and security analysis of the Model Context Protocol
img:
importance: 3
category: AI Security
---

The first **ProVerif-based formal security model** of the [Model Context Protocol (MCP)](https://modelcontextprotocol.io/), along with practical attack implementations that validate the formal findings on real MCP environments.

## Research Overview

1. **Formal Modeling** - ProVerif models of MCP protocol flows (initialization, tool discovery, sampling, OAuth 2.1, multi-server)
2. **Threat Verification** - Formal verification of four threat models:
   - Prompt Injection
   - Tool Poisoning
   - Data Leakage
   - Privilege Escalation
3. **Practical Attacks** - 8 attack scenarios implemented with the MCP Python SDK
4. **Mitigations** - Formal re-verification with proposed protocol-level defenses

## Project Structure

```
formal/          ProVerif formal models (.pv/.pvl files)
attacks/         Python attack implementations and MCP servers
paper/           LaTeX paper and artifacts
results/         Experimental results (generated)
docs/            Literature survey and documentation
scripts/         Top-level automation
```

## Significance

This project bridges my expertise in **formal verification** and **protocol security** with the emerging field of **LLM security**, demonstrating how traditional security analysis techniques can be applied to AI systems.
