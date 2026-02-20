# Fragment-DeNovo-Design

The RECAP Recombinator: Fragment-Based De Novo Drug Design from 1000 FDA Approved Drugs

## Overview
This repository implements **The RECAP Recombinator**, a computational tool for fragment-based *de novo* drug design. The core methodology involves deconstructing known FDA-approved drugs into molecular fragments using the **RECAP (Retrosynthetic Combinatorial Analysis Procedure)** algorithm, analyzing these fragments, and recombining them to generate novel, patent-free molecules with predicted desirable properties.

The workflow is optimized for **memory-constrained environments (8GB RAM)** by utilizing intermediate CSV storage and garbage collection.

## Features
- ✅ **Data Acquisition:** Retrieves FDA-approved small molecules from ChEMBL (max_phase=4).
- ✅ **RECAP Deconstruction:** Breaks drugs into synthetically accessible fragments.
- ✅ **Fragment Analysis:** Evaluates fragments using QED (Quantitative Estimate of Drug-likeness) and Synthetic Accessibility scores.
- ✅ **Recombination Engine:** Stochastically links fragments at dummy atom positions to create novel structures.
- ✅ **Multi-Objective Scoring:** Ranks molecules based on MW, LogP, TPSA, Lipinski's Rule of 5, and toxicity filters (PAINS, Brenk).
- ✅ **Memory Optimization:** Implements garbage collection and disk-based intermediate storage for large-scale generation.

## Requirements
- Python 3.8+
- 8GB RAM minimum (16GB recommended for large fragment libraries)

## Installation

pip install -r requirements.txt

## Methodology
Fetch Data: Query ChEMBL for FDA-approved small molecules.
Fragment: Apply RECAP decomposition to extract leaf nodes.
Filter: Remove fragments with poor QED or high synthetic complexity.
Recombine: Randomly pair fragments and form bonds at dummy atoms (*).
Score: Calculate physicochemical properties and filter for toxicity alerts.
Rank: Sort by desirability score (weighted sum of properties).
