# SNN Memory Engram Simulation

**A simplified Python implementation of the spiking neural network model from Tomé et al. (Nature Neuroscience, 2024)**

[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## Overview

This repository contains a **simplified Python implementation** of the spiking neural network model used in the paper:

> *Dynamic and selective engrams emerge with memory consolidation* – Tomé, D. F., Zhang, Y., Aida, T., et al. *Nature Neuroscience*, 27, 561–572 (2024).

The model simulates the **dentate gyrus (DG)** of the hippocampus and implements the three phases of memory formation:
- **Encoding** – Formation of initial memory engram via Hebbian excitatory plasticity
- **Consolidation** – Refinement of memory via inhibitory STDP (CCK+ interneurons)
- **Recall** – Testing memory selectivity with novel stimuli

## Key Implemented Mechanisms

| Component | Implementation | Paper Reference |
|-----------|----------------|-----------------|
| Excitatory neuron | AIF2I model (adaptive integrate-and-fire with 2 adaptation variables) | Eq. (1)-(4) |
| Inhibitory neuron | Simple IF model (no adaptation, no dynamic threshold) | Methods – Neuron model |
| AMPA/NMDA conductance | Dual-component excitatory postsynaptic conductance | Eq. (5)-(7) |
| Short-term plasticity | Variables `x` (vesicle availability) and `u` (release probability) | Eq. (8)-(9) |
| Excitatory STDP | Triplet STDP + heterosynaptic + transmitter-induced plasticity | Eq. (10)-(14) |
| Inhibitory STDP | Global activity-dependent plasticity (H(t) – γ) | Eq. (15)-(17) |

## Experiments Implemented

The notebook reproduces three key experiments from the paper:

| Experiment | Hypothesis | Corresponding Figure |
|------------|------------|----------------------|
| **Exp 1** | Selectivity increases with consolidation time | Fig. 1j |
| **Exp 2** | Blocking CCK+ interneurons during recall disrupts selectivity | Fig. 5f-g |
| **Exp 3** | Inhibitory plasticity during consolidation is necessary for selectivity | Fig. 6a-d |

## Sample Output

Running the notebook generates three key visualizations:

1. **Selectivity vs. Consolidation Time** – Shows how the discrimination index increases as memory consolidates
2. **Engram Composition Changes** – Visualizes neuron dropout and recruitment after 24 hours
3. **CCK+ Block Effect** – Demonstrates that blocking CCK+ inhibition during recall eliminates memory selectivity

## Requirements

```bash
pip install numpy matplotlib
