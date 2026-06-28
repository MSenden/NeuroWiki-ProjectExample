---
type: phenomenon
title: Figure-Ground Segregation
confidence: established
updated: 2026-06-28
related:
  - REG_v1
  - THE_binding-by-synchrony
  - PHE_gamma-synchrony
  - MOD_kuramoto-v1-oscillator
  - PAR_texture-figure-ground-discrimination
tags: []
---

# Figure-Ground Segregation

## Description

Figure-ground segregation is the perceptual ability to distinguish a figure region from its background based on differences in visual features such as texture, contrast heterogeneity, orientation, spatial frequency, color, or element proximity. It is one of the canonical computations performed by early visual cortex, with neural correlates in V1 and V4 (@Lamme1995†, @Poort2016†).

## Empirical Basis

Figure-ground segregation depends on statistical differences between figure and ground across one or more feature dimensions; contrast heterogeneity, spatial frequency, orientation, color, and element proximity all drive segregation (@Hadjipapas2015†, @Henrie2005†). Global population statistics differences between figure and ground (rather than local boundary signals alone) determine discrimination accuracy (@Roelfsema2002†).

In macaque V1 and V4, texture segregation elicits figure enhancement in the figure region followed by ground suppression, with the later ground suppression in V4 requiring recurrent processing (@Poort2016†). V1 neurons show enhanced responses to figure regions relative to ground with a delay (~100 ms) consistent with feedback processing (@Lamme1995†). This figure-ground modulation (FGM) is causally necessary for perception: optogenetic silencing of the late V1 response (after feedforward, beginning ~100 ms post-onset) in mice abolished texture figure-ground discrimination but left simple grating detection intact, whereas silencing during the early feedforward response caused general visual impairment (@Roelfsema2023). Pyramidal cells and VIP interneurons show positive FGM; SST interneurons show reversed FGM, consistent with a disinhibitory circuit where VIP cells suppress SST cells to reduce surround suppression for figure elements (@Roelfsema2023).

Human psychophysics with Gabor-annulus texture stimuli demonstrates that discrimination accuracy follows an Arnold tongue pattern in the space of contrast heterogeneity (within-figure feature similarity) and grid coarseness (inter-element spacing). Both factors reduce accuracy independently: a one-standard-deviation increase in contrast heterogeneity reduces discrimination odds by 44% (OR = 0.56, 95% HDI [0.41, 0.74]) and a one-SD increase in grid coarseness reduces odds by 23% (OR = 0.77, 95% HDI [0.67, 0.88]). Their interaction is synergistic (OR = 1.27, 95% HDI [1.12, 1.44]) (@Karimian2025).

Perceptual learning over 8 daily sessions improves figure-ground discrimination systematically: discrimination accuracy increases with session (β = 0.095, OR = 1.10, 95% HDI [1.07, 1.13], Pr[β>0] = 1.00). This learning is retinotopically specific: transfer session performance (figure moved to new quadrant) is practically equivalent to session 2 performance (93% posterior probability of practical equivalence), not to late-training performance (@Karimian2025).

## Key Parameters and Quantitative Signatures

- OR for contrast heterogeneity (per SD increase): 0.56 [0.41, 0.74] — reduces accuracy (@Karimian2025)
- OR for grid coarseness (per SD increase): 0.77 [0.67, 0.88] — reduces accuracy (@Karimian2025)
- OR for contrast heterogeneity × grid coarseness interaction: 1.27 [1.12, 1.44] — synergistic effect (@Karimian2025)
- OR for session (per mean-centered unit): 1.10 [1.07, 1.13] — accuracy improves with training (@Karimian2025)
- 75% accuracy boundary: triangular Arnold tongue region in contrast heterogeneity × grid coarseness space (@Karimian2025)
- Transfer session (session 9) accuracy equivalent to session 2, not sessions 7–8 (93% posterior probability of equivalence) (@Karimian2025)

## Generality

Figure-ground segregation is documented across species (cat, macaque, human), visual field locations, and recording modalities. The specific behavioral parameters reported above are for healthy human adults (n = 8, age 23.75 ± 6.45) using Gabor-annulus texture stimuli. Effects in complex natural scenes remain untested under the TWCO framework. Disrupted figure-ground segregation has been documented in schizophrenia, linked to abnormal gamma synchrony (@Uhlhaas2008†).

## Controversies

### Mechanism: synchrony-based vs. rate-based grouping

- **Position A**: Gamma synchrony among V1 assemblies mediates figure-ground segregation by selectively grouping assemblies encoding figure elements with similar features and proximate cortical locations (@Karimian2025, @Roelfsema2004†).
- **Position B**: Enhanced mean firing rate in figure regions, implemented by recurrent processing and feedback, mediates segregation without requiring synchrony (@Roelfsema1998†, @Roelfsema2023, @Roelfsema2002†). Key evidence: optogenetic silencing of late V1 activity specifically disrupts texture figure-ground discrimination (not simple detection), demonstrating causal necessity of the FGM response (@Roelfsema2023). The FGM signal propagates from V1 via corticocortical connections to bind texture elements across the figure region at all spatial scales (@Roelfsema2023).
- **Possible resolution**: Karimian et al. 2025 showed that synchrony outperforms rate-based readouts extracted from the same V1 oscillator model in predicting human behavior, but did not compare against a dedicated BBRE model architecture. The optogenetic result is consistent with either hypothesis: the late recurrent response could carry synchrony or rate information. Distinguishing these would require recording the oscillatory structure of the late V1 response.
- **Status**: unresolved
- **⚑ Human review requested**: This is the central open question of the project.

## Modeling Implications

Models of figure-ground segregation must account for: (1) sensitivity to contrast heterogeneity and element proximity; (2) Arnold tongue structure of behavioral accuracy; (3) retinotopically specific perceptual learning; (4) delayed figure enhancement in V1 consistent with recurrent processing. See [[MOD_kuramoto-v1-oscillator]], [[THE_binding-by-synchrony]], [[THE_weakly-coupled-oscillators]].
