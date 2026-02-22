---
layout: page
title: Rylee - Chess Engine
permalink: /projects/rylee/
repo_url: https://github.com/funkybooboo/rylee
description: A chess bot designed to mimic human behavior using AI techniques.
---

**Repository:** [github.com/funkybooboo/rylee](https://github.com/funkybooboo/rylee)

An advanced chess engine designed to mimic human playing behavior using AI techniques and machine learning. Unlike traditional engines optimized for perfect play, Rylee captures the nuances of human decision-making to create a more realistic and educational opponent.

## Goals

*   **Human-like Play:** Simulate natural mistakes and strategic patterns common to human players
*   **Adaptive Difficulty:** Adjust gameplay style based on opponent's skill level
*   **Educational Value:** Provide learning players with realistic, relatable opponents

## Implementation Details

Rylee utilizes advanced AI techniques to evaluate board states. Unlike traditional engines that rely solely on Minimax and Alpha-Beta pruning for optimal play, Rylee incorporates:

*   **Probabilistic Models:** Choose moves that a human of a certain rating might select
*   **Pattern Recognition:** Identify common human strategic patterns and mistakes
*   **Machine Learning:** Train on human game databases to capture realistic play styles
*   **Rating-Based Behavior:** Adjust decision-making based on target player strength

## Technology Stack

*   **Language:** Python
*   **AI/ML:** PyTorch, reinforcement learning
*   **Chess Logic:** Custom board representation and move generation
*   **Training Data:** Human game databases for realistic behavior modeling
