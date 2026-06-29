---
type: model
title: Kuramoto Phase Oscillator Model of V1 (Karimian et al., 2025)
explanatory_character: mechanistic
marr_level:
  - computational
  - algorithmic
construction: theory-derived
exploratory: false
confidence: speculative
updated: 2026-06-29
related:
  - THE_weakly-coupled-oscillators
  - THE_binding-by-synchrony
  - PHE_gamma-synchrony
  - REG_v1
  - PHE_figure-ground-segregation
  - PAR_texture-figure-ground-discrimination
tags: []
---

# Kuramoto Phase Oscillator Model of V1

## Description

A network of $N = 400$ weakly coupled phase oscillators arranged on a 20 × 20 irregular grid on the cortical surface, representing a 6.7° × 6.7° patch of V1 corresponding to the figure region of the texture stimuli (@Karimian2025). Each oscillator represents a neural assembly whose phase evolves according to Kuramoto dynamics with an intrinsic frequency determined by local stimulus contrast and coupling strengths set by cortical distance. The model derives a synchrony-based prediction of figure-ground discrimination accuracy and, augmented with a Hebbian learning rule, predicts session-by-session improvements in perceptual learning (@Karimian2025).

## Descriptive Target

The model targets the triangular Arnold tongue of human figure-ground discrimination accuracy (≥75% correct) in contrast heterogeneity × grid coarseness space, with the synchrony-derived boundary matching the behavioral boundary (@Karimian2025). A stimulus configuration that does not produce a triangular synchrony boundary in this space would falsify the model with respect to its primary descriptive target. Secondary target: session-by-session improvement in discrimination accuracy over 8 sessions, predicted by Hebbian increases in lateral coupling strengths (@Karimian2025).

## Explanatory Scope

At the level of abstract phase oscillators (neural assemblies treated as single-frequency units), the model is mechanistic: it specifies how intrinsic frequency dispersion (driven by contrast heterogeneity), distance-dependent coupling, and network size jointly determine zero-lag synchrony and thereby discrimination accuracy. The Arnold tongue structure and learning-induced synchrony increases emerge from the dynamics rather than being imposed.

At the biophysical level — single-neuron spike dynamics, the E-I circuit mechanisms generating gamma oscillations, downstream coincidence detection — the model is phenomenological: each assembly is reduced to a scalar phase variable with no specification of spiking activity, excitatory-inhibitory balance, or conductance dynamics.

The Hebbian learning rule is mechanistic at the oscillator-coupling level but phenomenological at the synaptic level: it does not specify which synapse types are modified, through what molecular pathway, or the direction of synaptic change.

## Formal Description

**Phase dynamics** (Kuramoto network, session $s$):

$$\dot{\theta}_i = \omega_i + \frac{1}{N}\sum_{j=1}^{N} K_{ij}^s \sin(\theta_j - \theta_i), \quad i = 1, \ldots, N;\; s = 1, \ldots, 9 \tag{1}$$

where $\theta_i$ is the phase of oscillator $i$, $\omega_i = 2\pi\nu_i$ its intrinsic angular frequency, and $K_{ij}^s$ the coupling strength between oscillators $i$ and $j$ in session $s$ (note: $s$ is a session index, not an exponent).

**Intrinsic frequency** (quasi-linear function of local contrast, Hz):

$$\nu_i = 25 + 0.25\, C_i \tag{2}$$

Empirically established in macaque V1 for luminance contrast (@Roberts2013†, @Zachariou2021†). Yields frequencies in the range ~25–50 Hz across the 0–100% contrast range.

**Local RMS contrast** within receptive field:

$$C_i = \sqrt{\left(\sum_{h=1}^{M} w_{ih} \frac{(L_h - \bar{L})^2}{\bar{L}^2}\right) \bigg/ \sum_{h=1}^{M} w_{ih}} \tag{3}$$

where $L_h$ is pixel luminance, $\bar{L}$ is mean luminance, and $w_{ih}$ is the Gaussian receptive field weight of oscillator $i$ for pixel $h$.

**Gaussian receptive field weighting**:

$$w_{ih} = \exp\!\left(-\frac{(x_h - X_i)^2 + (y_h - Y_i)^2}{2\sigma_i^2}\right) \tag{4}$$

Receptive field diameter scales with eccentricity $e$: $\varnothing = \max(0.172e - 0.25,\, 1)$ degrees (@Freeman2011†). Standard deviation $\sigma_i = \varnothing/4$.

**Initial coupling strength** (exponential decay with cortical distance $d_{ij}$):

$$K_{ij}^1 = \gamma\, e^{-\lambda d_{ij}} \tag{5}$$

Parameters $\gamma = 24.63$ (maximum coupling strength) and $\lambda = 0.22$ (coupling decay factor) estimated by (@Karimian2025) from the interaction strength vs. cortical distance relationship in macaque V1 (@Lowet2017); not fit to behavioral data.

**Psychometric function** (synchrony to accuracy):

$$P_c = \frac{1}{1 + \exp(-\mu_0 - \mu_1\, r)} \tag{6}$$

where $r = \left|\frac{1}{N}\sum_j \exp(i\theta_j)\right|$ is the Kuramoto order parameter quantifying zero-lag synchrony.

**Hebbian learning** (offline between sessions): Coupling strengths $K_{ij}^s$ are updated between sessions using pairwise phase-locking values (PLVs) (@Lachaux1999†) accumulated over trials within a session, weighted by the per-trial probability of a correct response. Connections between oscillators that exhibited coherence on correct trials are strengthened, bounded above by $\gamma$. This oscillation-based Hebbian mechanism is biologically motivated by spike-timing dependent plasticity (@Masquelier2009†).

## Core Assumptions

- **Linear frequency–contrast mapping**: Oscillator intrinsic frequency is a linear function of local contrast.
  - *Biological justification*: Empirically validated in macaque V1 LFP and MEG recordings (@Roberts2013†, @Hadjipapas2015†, @Zachariou2021†).
  - *When violated*: If the relationship is non-linear or substantially different in humans, model detuning values will be miscalibrated.

- **Exponential coupling decay**: Coupling between assemblies decays exponentially with cortical distance.
  - *Biological justification*: Consistent with the spatial structure of lateral horizontal connections in V1 (@Gilbert1983†, @Stettler2002†, @Lowet2017).
  - *When violated*: Human horizontal connections may extend further than macaque, suggesting a slightly smaller $\lambda$ for humans (@Boucsein2011†, @Lowet2017). The chosen parameter fell just outside the optimal region when assessed with weighted Jaccard similarity (@Karimian2025).

- **Figure-only simulation**: Only the figure region is simulated; background synchrony is fixed at the maximum contrast heterogeneity level.
  - *Biological justification*: Additional simulations including the background confirmed that a coherent figure assembly emerges against a noisy surround (@Karimian2025).
  - *When violated*: Background activity modulating figure synchrony through inter-region interactions is not captured.

- **Instantaneous frequency as firing rate proxy**: $\dot{\theta}_i / 2\pi$ is treated as a proxy for instantaneous population firing rate of the corresponding assembly.
  - *Biological justification*: Gamma frequency and firing rate co-vary approximately linearly over the contrast range relevant to these stimuli (@Zachariou2021†).
  - *When violated*: At very high or low firing rates, frequency and rate decouple; population firing rates are generally much lower than gamma frequencies (@Zachariou2021†).

- **Local learning**: Plasticity acts on lateral connections within V1 and is specific to trained retinal locations.
  - *Biological justification*: Location-specific perceptual learning has been attributed to plasticity in early visual areas (@Karni1997†). Transfer session data confirm location-specificity in participants (@Karimian2025).

## Empirical Support

- Human behavioral discrimination accuracy follows a triangular Arnold tongue in contrast heterogeneity × grid coarseness space, matching the Arnold tongue structure of model synchrony (@Karimian2025).
- One SD increase in model synchrony corresponds to OR = 2.19 (95% HDI [1.38, 3.33]) for correct response (@Karimian2025).
- Pearson correlation between simulated and behavioral Arnold tongues: ~0.65–0.85 across sessions; weighted Jaccard similarity: ~0.45–0.60, approaching noise ceiling (89% of maximum achievable correlation; 79% of maximum Jaccard) (@Karimian2025).
- Simulated Arnold tongue size predicts behavioral Arnold tongue size across training sessions 3–8 (β = 0.54, 95% HDI [0.106, 0.935], Pr[β>0] = 0.992) (@Karimian2025).
- Model parameters ($\gamma$, $\lambda$) set a priori from macaque data fell within the near-optimal region of parameter space for predicting human behavior (@Karimian2025).
- Synchrony outperforms both average figure firing rate (Δ ELPD ≈ 127, stacking weight ~0) and figure-background rate difference (ΔELPD ≈ 19, stacking weight 0.10) in out-of-sample accuracy (synchrony stacking weight = 0.90) (@Karimian2025).

## Empirical Challenges

- No direct electrophysiological data from human participants during the task; the gamma-band interpretation rests on macaque physiology (@Karimian2025).
- Model oscillator frequencies are in the gamma band by construction (via equation 2), but the paper does not directly verify that model unit frequencies match experimentally observed gamma for the specific stimuli used (noted by reviewers; @Karimian2025).
- Synchrony and stimulus features are near-collinear in this model ($R^2 \approx 0.8$), making synchrony difficult to dissociate from a deterministic feature transformation (@Karimian2025).
- Coupling decay parameter $\lambda = 0.22$ from macaque may overestimate the decay in humans; a smaller $\lambda$ would improve model fit (@Lowet2017, @Boucsein2011†, @Karimian2025).

## Comparison to Alternatives

- **Rate readouts from same model**: Average figure firing rate is insensitive to coupling changes (average effective firing rate identical to intrinsic across all conditions, differing by < 10⁻¹² Hz), making it non-viable for explaining learning effects. Figure-background rate difference shows a meaningful but smaller association (OR = 0.58) and worse out-of-sample prediction than synchrony (@Karimian2025).
- **Binding by Enhanced Firing** (@Roelfsema2023): A dedicated implementation was not tested. This is an acknowledged gap and a direction for future comparison.

## Controversies

The broader debate on whether gamma synchrony or firing rate mediates figure-ground segregation is covered in [[THE_binding-by-synchrony]] and [[PHE_gamma-synchrony]].

## Usage in the Literature

Karimian et al. 2025 used this model to generate quantitative predictions of human figure-ground discrimination accuracy and perceptual learning across 8 sessions in a texture task. The model extends earlier coupled oscillator V1 models (@Lowet2015, @Lowet2017) by adding a Hebbian plasticity component and testing predictions against human psychophysics. Psychophysical dataset and code are publicly available (Karimian et al., 2024, Zenodo, https://doi.org/10.5281/zenodo.10817187; GitHub: https://github.com/ccnmaastricht/NeuralSynchrony-FigureGround).
