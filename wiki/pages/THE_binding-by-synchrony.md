---
type: theory
title: Binding by Synchrony
status: active-research-area
updated: 2026-06-28
related:
  - PHE_gamma-synchrony
  - MOD_kuramoto-v1-oscillator
  - THE_weakly-coupled-oscillators
  - PHE_figure-ground-segregation
  - REG_v1
  - PAR_texture-figure-ground-discrimination
tags: []
---

# Binding by Synchrony

## Core Claims

Binding by Synchrony (BBS) holds that the visual system solves the binding problem by synchronizing the firing of neural assemblies encoding features belonging to the same object, while keeping assemblies for different objects desynchronized (@Singer1999†). Early proposals centered on gamma-band (30–80 Hz) oscillations as the temporal substrate, with foundational empirical support from stimulus-specific gamma oscillations in cat V1 orientation columns (@Gray1989†, @Singer1999†, @Fries2009†). The Communication through Coherence (CTC) extension holds that gamma synchrony between areas enables selective routing of neural signals, such that a sending area's output reaches a receiving area only when they are phase-locked (@Fries2015†). The theory implies that synchrony, rather than mean firing rate, is the primary signal carrying grouping information to downstream areas.

## Explanatory Schema

BBS invokes temporal coincidence detection: downstream neurons receiving synchronized input from multiple assemblies preferentially integrate that input, effectively reading out shared object membership through phase-locking. The explanatory pattern is: stimulus features → gamma oscillations with feature-dependent frequency → selective synchrony among similar-feature proximate assemblies → perceptual grouping via coincidence detection. Under the TWCO extension of BBS (see [[THE_weakly-coupled-oscillators]]), the stimulus-dependence of gamma frequency is recast as the mechanism that *achieves* selective synchrony rather than undermining it.

## Model Family

The primary formal instantiation relevant to this project is the Kuramoto-type V1 phase oscillator network of Karimian et al. 2025, implementing BBS via TWCO ([[MOD_kuramoto-v1-oscillator]], [[THE_weakly-coupled-oscillators]]). Earlier coupled oscillator models were applied to image segmentation (@Baldi1990†) and V1 gamma dynamics (@Lowet2015, @Lowet2017). These models share the feature that synchrony emerges from the interplay of contrast-driven frequency dispersion and distance-limited lateral coupling.

## Mechanistic Grounding

BBS operates at the level of inter-assembly phase relationships. It does not specify the single-neuron biophysics generating gamma oscillations but assumes that local E-I circuit mechanisms sustain oscillations at frequencies set by the local stimulus (@Hadjipapas2015†, @Roberts2013†). Inter-assembly coupling is mediated by lateral horizontal connections in V1 whose strength decays with cortical distance (@Gilbert1983†, @Stettler2002†, @Boucsein2011†). The mechanism by which downstream areas decode phase-locking remains underspecified; BBS assumes but does not implement a coincidence detector.

## Empirical Scope

BBS is proposed to explain figure-ground segregation (@Karimian2025, @Roelfsema2004†), feature binding across spatially distributed assemblies (@Womelsdorf2007†), and perceptual grouping effects correlated with synchrony changes (@Melloni2007†). It is primarily scoped to early visual cortex (V1, possibly V4) and spatially structured visual stimuli. It does not fully address attentional modulation, though synchrony interacts with attentional gain control and attention selectively synchronizes inter-areal gamma to facilitate stimulus selection (@Womelsdorf2007†, @Bosman2012†).

Karimian et al. 2025 provides quantitative psychophysical support: human figure-ground discrimination in texture stimuli follows the Arnold tongue pattern predicted by model gamma synchrony, and perceptual learning over 8 sessions mirrors predicted synchrony increases. Synchrony outperforms rate-based model readouts in out-of-sample predictive accuracy (synchrony stacking weight = 0.90) (@Karimian2025).

## Controversies

### Binding by Synchrony vs. Binding by Enhanced Firing

- **Position A**: Gamma synchrony among assemblies mediates binding; synchrony carries the grouping signal (@Singer1999†, @Fries2009†, @Karimian2025).
- **Position B (BBRE)**: Neural assemblies bind by enhanced firing rate triggered by recurrent/feedback processing; synchrony is not required and is too weak to carry grouping information across regions or across more than a few mm within V1 (@Roelfsema1998†, @Roelfsema2023). The foundational observation is that V1 neurons show firing rate enhancement for contour elements of the attended target curve over the distractor, with this enhanced-firing label propagating from the fixation point along the curve in macaque V1 (@Roelfsema1998†). Roelfsema2023 (a Perspective, not primary empirical data) marshals four specific lines of evidence: (1) V1 synchrony during macaque contour tracing was extremely weak (cross-correlation peak coefficients ~0.01) and absent entirely in 1 of 3 monkeys, with strength indistinguishable for neurons on the same vs. different curves (@Roelfsema2023); (2) optogenetic experiments in mouse V1 showed behavioral detection was equally effective for synchronous (3 ms) and asynchronous (100 ms) stimulation with the same total energy, demonstrating that synchrony provides no integration advantage up to 100 ms (@Roelfsema2023); (3) figure-ground modulation (FGM) — enhanced firing rates for figure over ground — is causally necessary for figure-ground perception: optogenetic silencing of the late V1 response (after feedforward, ~100 ms) specifically abolished figure-ground discrimination while leaving simple grating detection intact (@Roelfsema2023); (4) perceptual grouping occurs serially, one object at a time, consistent with a single enhanced-activity label rather than multiple simultaneous synchrony patterns (@Roelfsema2023). Texture figure-ground segregation (as in @Karimian2025) is explicitly cited as a paradigm where V1 FGM, not synchrony, underlies perception (@Roelfsema2023).
- **Possible resolution**: Rate-based readouts from the Karimian2025 V1 oscillator model perform worse than synchrony in out-of-sample accuracy. However, these comparisons used readouts extracted from a single oscillator model, not a dedicated BBRE architecture. A full head-to-head comparison with an independent rate-based model implementing BBRE remains to be conducted.
- **Status**: unresolved
- **⚑ Human review requested**: Whether synchrony or rate is the primary mechanism for figure-ground segregation is the central open question of this project.

### Stimulus-dependence of gamma as a challenge to BBS

- **Position A**: Because gamma frequency varies with local stimulus features, assemblies encoding different features of the same object oscillate at different frequencies, preventing the stable synchrony required by BBS (@Ray2010, @Ray2015†, @Shirhatti2022†).
- **Position B**: TWCO reframes this as a feature: assemblies with similar features have similar frequencies and synchronize; assemblies with different features do not. This makes BBS consistent with stimulus-dependent gamma (@Lowet2015, @Lowet2017, @Karimian2025).
- **Status**: unresolved; direct electrophysiological evidence from humans during figure-ground tasks is absent.

## Key Sources

Foundational empirical demonstration of stimulus-specific gamma: (@Gray1989†). Foundational proposal: (@Singer1999†). Gamma as fundamental cortical process and CTC framework: (@Fries2009†, @Fries2015†). Contour grouping and synchrony in V1: (@Roelfsema2004†). Cross-cortical synchrony and perception: (@Melloni2007†, @Womelsdorf2007†). Inter-areal attention-dependent synchrony: (@Bosman2012†). Foundational BBRE empirical evidence: (@Roelfsema1998†). Challenge from rate-based alternative: (@Roelfsema2023). Psychophysical and computational support via TWCO: (@Karimian2025).
