---
type: paradigm
title: Texture Figure-Ground Discrimination (Karimian et al., 2025)
updated: 2026-06-28
related:
  - PHE_figure-ground-segregation
  - PHE_gamma-synchrony
  - MOD_kuramoto-v1-oscillator
  - REG_v1
tags: []
---

# Texture Figure-Ground Discrimination Paradigm

## Description

Participants report the orientation (horizontal vs. vertical) of a rectangular figure region defined by reduced contrast heterogeneity within an otherwise uniform-statistics texture stimulus. The full-screen stimulus consists of non-overlapping Gabor annuli on an irregular grid; figure and background differ only in the statistical spread of local contrast values, with mean contrast equalized across regions. Two parameters are manipulated orthogonally: contrast heterogeneity within the figure ($\zeta$) and grid coarseness ($\rho$), implementing TWCO frequency detuning and coupling strength proxies, respectively (@Karimian2025).

## What It Measures / Reveals

The paradigm provides a behavioral readout of the interplay between gamma frequency detuning (contrast heterogeneity) and lateral coupling strength (element spacing) in V1. Discrimination accuracy as a function of $\zeta$ and $\rho$ reveals whether perceptual segregation follows the Arnold tongue structure predicted by TWCO (@Karimian2025).

The multi-session design (8 training + 1 transfer) additionally measures perceptual learning curves and tests their retinotopic specificity, enabling comparison with model predictions of learning-induced changes in lateral coupling strength (@Karimian2025).

## Standard Variants

- **Static (Session 1 only)**: 25 conditions (5 levels × 5 levels of $\zeta$ and $\rho$), 750 trials. Tests TWCO predictions for naive observers without learning effects.
- **Training version (Sessions 1–8)**: 8 consecutive daily sessions; measures learning trajectory and allows model fitting of learning parameters.
- **Transfer session (Session 9)**: Figure moved to diagonally opposite visual quadrant (lower right → upper left). Tests location-specificity of learning; participants informed of displacement but not told target quadrant.

## Stimulus Parameters

| Parameter | Value |
|-----------|-------|
| Gabor annulus diameter | 0.7° |
| Spatial frequency | 5.7 cycles/degree |
| Mean luminance | 60.76 Cd/m² (on 60.76 Cd/m² grey background) |
| Figure eccentricity | 7 ± 1° (always within one visual quadrant) |
| Figure size | 6.7° × 6.7° (square) |
| Contrast heterogeneity $\zeta$ | {0.01, 0.2575, 0.505, 0.7525, 1.0} |
| Grid coarseness $\rho$ | {1, 1.125, 1.250, 1.375, 1.500} |
| Background heterogeneity | Fixed at maximum ($\zeta = 1$) |
| Conditions | 25 (all $\zeta \times \rho$ combinations) |
| Trials per session | 750 (30 blocks × 25 trials/block, random order) |
| Display | 19" Samsung SyncMaster 940BF, 60 Hz, 1280 × 1024, 57 cm viewing distance |
| Eye tracking | Eyelink 1000, 500/1000 Hz, < 0.01° RMS spatial resolution |

Contrast heterogeneity $\zeta$ is operationalized as the half-width of a uniform distribution $U[0.5 - \zeta/2,\; 0.5 + \zeta/2]$ from which figure element contrasts are drawn. Background elements have contrasts drawn from $U[0, 1]$ (maximum heterogeneity). $\rho$ scales the mean center-to-center distance between neighboring annuli (@Karimian2025).

## Limitations and Confounds

- Highly controlled stimuli (Gabor annuli on irregular grid) are far removed from natural scenes; generalizability to naturalistic stimuli is unknown (@Karimian2025).
- Mean contrast is equalized between figure and background, but the absence of high-contrast Gabors in the figure (relative to background when $\zeta < 1$) represents a potential luminance-variance cue. This is inherent to the design and acknowledged (@Karimian2025).
- Transfer session: participants were informed of the figure's quadrant displacement but not told the target quadrant; visual search effects cannot be fully excluded, though these would affect only a small number of trials (@Karimian2025).
- First-session data may partly reflect non-perceptual learning (task familiarization, fixation strategy, stimulus-response mapping); session 2 was used as the early reference for transfer comparisons (@Karimian2025).
- No neuroimaging or EEG/MEG recordings; mechanistic interpretation (gamma synchrony in V1) is theoretically inferred from the model, not directly measured in participants (@Karimian2025).

## Key Studies

Primary source: (@Karimian2025). Psychophysical dataset: Karimian M, Roberts MJ, De Weerd P, Senden M (2024), Zenodo, https://doi.org/10.5281/zenodo.10817187. Analysis code: https://github.com/ccnmaastricht/NeuralSynchrony-FigureGround. Stimulus code: https://github.com/ccnmaastricht/TextureStimuli-FigureGround.

## Relevance to This Project

This is the primary empirical paradigm linking gamma synchrony principles (TWCO) to human perceptual behavior. The Arnold tongue structure of behavioral data, its quantitative match to model synchrony from the [[MOD_kuramoto-v1-oscillator]], and the retinotopically specific learning effects constitute the main empirical pillars of the project's claim that gamma synchrony principles are functionally relevant to figure-ground segregation.
