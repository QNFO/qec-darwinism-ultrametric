---
title: "Archimedean Shadows: The QEC-Darwinism Tradeoff in Ultrametric Spaces"
author: "Rowan Brad Quni-Gudzinas"
date: "2026-08-05"
license: "QNFO Unified License Agreement (QNFO-ULA)"
doi: "TBD"
status: "draft"
keywords: ["quantum error correction", "quantum darwinism", "ultrametric", "bruhat-tits tree", "p-adic", "ostrowski"]
---

# Archimedean Shadows: The QEC-Darwinism Tradeoff in Ultrametric Spaces

> **Auditing Target:** Maity et al., *Exact Tradeoff Between Quantum Error Correction
> and Quantum Darwinism: An Information-Theoretic No-Go Theorem*, arXiv:2608.03944v1 (2026).

## Abstract

[TBD — draft after §1–4 are complete. 150–250 words.]

---

## 1. Introduction: A Tradeoff Born in One Completion

Quantum error correction (QEC) and Quantum Darwinism describe opposing consequences
of the same physical process — system-environment interaction. QEC seeks to preserve
logical quantum information against decoherence; Quantum Darwinism explains how
decoherence itself produces the objective, classical world by proliferating
redundant records into the environment.

Maity et al. (arXiv:2608.03944) have established the first quantitative connection
between these paradigms: an exact information-theoretic tradeoff

$$R(f) \cdot F_L \leq C$$

where $R(f)$ is Darwinistic redundancy (the number of environment fragments that
carry the full system information) and $F_L$ is the post-recovery logical fidelity
(how well the logical qubit survives after syndrome extraction and correction).
A model-independent no-go theorem further shows that $F_L$ exceeding a critical
threshold $F_L^{\text{crit}}$ precludes redundant classical records entirely.

The authors derive this tradeoff using a block-environment model based on the
logical GHZ block of the Shor [[9,1,3]] code. All quantities — fidelity, Holevo
information, redundancy — are defined over standard Archimedean metrics: the
Hamming distance between codewords, the trace distance between density matrices,
the Shannon-like counting of distinct environment fragments.

**This paper asks: what happens to the tradeoff when the code space is structured
ultrametrically rather than Archimedeanly?**

The question is not idle. Per Ostrowski's theorem, any quantity defined over the
rationals $\mathbb{Q}$ has completions at every place — the real Archimedean place
$\mathbb{R}$ and all $p$-adic non-Archimedean places $\mathbb{Q}_p$. The
Bruhat-Tits tree is the natural geometry for $p$-adic information: a homogeneous
tree where distances satisfy the strong triangle inequality

$$d(x,z) \leq \max(d(x,y), d(y,z))$$

rather than the Archimedean $d(x,z) \leq d(x,y) + d(y,z)$. This changes the
information topology fundamentally: in an ultrametric, two points are either
identical or maximally distant relative to any third — there is no "partial"
overlap, no gradual degradation. The concept of "redundancy" — how many
distinct environment fragments carry the same system information — acquires a
different meaning when fragments cannot be partially similar.

This paper is an exercise in consilience: it brings the Continuum Trilogy's
Ostrowski diagnostics to bear on a precise, falsifiable no-go theorem in quantum
information theory. The result — whether the tradeoff changes or proves
Ostrowski-invariant — is a concrete empirical question about the relationship
between the number system and the physics built on it.

### 1.1 Structure

- **§2** summarizes the Maity et al. theorem: model, derivation, and the no-go bound
- **§3** introduces ultrametric code spaces: Bruhat-Tits geometry, p-adic sphere
  packings, and the Continuum Trilogy connection
- **§4** reformulates redundancy in ultrametric terms and derives how the tradeoff
  relation transforms
- **§5** discusses implications: could ultrametric QEC circumvent the Darwinism
  bottleneck? What would an experiment look like?
- **§6** states falsifiable predictions and concludes

---

## 2. The No-Go Theorem (Summary of Maity et al.)

The Maity et al. framework is the first quantitative connection between QEC and
Quantum Darwinism. We summarize it here as the *auditing target* — the
Archimedean theorem whose ultrametric transformation is the subject of this paper.

### 2.1 The Block-Environment Model

A logical qubit is encoded in one GHZ block of the Shor [[9,1,3]] code. The
logical basis is formed by the orthogonal codewords

$$|\bar{z}_{\pm}\rangle_b = \frac{|000\rangle \pm |111\rangle}{\sqrt{2}},$$

while each of $N$ environment qubits is initialized in $|+\rangle = (|0\rangle + |1\rangle)/\sqrt{2}$.
The block interacts with the environment through the Hamiltonian

$$\hat{H} = g_Z \hat{Z}_b \otimes \hat{S}_Z + g_X \hat{X}_b \otimes \hat{S}_X,$$

where $\hat{S}_Z = \sum_{k=1}^N Z_k$ and $\hat{S}_X = \sum_{k=1}^N X_k$ are collective
spin operators. The exactly solvable limit is $g_X = 0$ (commuting sector); the
full Hamiltonian with $g_X \neq 0$ is treated numerically to confirm robustness.

### 2.2 Key Quantities (All Archimedean)

| Quantity | Symbol | Expression |
|:---------|:-------|:-----------|
| Logical fidelity | $F_L(N)$ | Post-recovery overlap with initial logical state; function of $g_Z, t, N$, and imperfect recovery efficiency $\eta$ |
| Bare logical fidelity | $F_{\text{bare}}$ | $F_{\text{bare}} = (F_L(N) - \eta)/(1-\eta)$ — fidelity before syndrome extraction |
| Holevo information | $\chi(F)$ | Accessible classical information about the system in environment fragment $F$ |
| Darwinistic redundancy | $R_\delta$ | $\#\{F \subset E : \chi(F) \geq (1-\delta) \ln 2\}$ — number of distinct non-overlapping fragments carrying near-complete classical information |
| Darwinism threshold | $\delta$ | Typical value $\delta = 0.10$ |
| Recovery efficiency | $\eta$ | Imperfect syndrome extraction efficiency; typical value $\eta = 0.60$ |

### 2.3 Lemma 1 — Block Entropy Bound (Archimedean)

For any qubit block state $\rho_B$ with bare logical fidelity $F_{\text{bare}} =
\langle \bar{z}_+ | \rho_B | \bar{z}_+ \rangle$, the von Neumann entropy satisfies

$$S(\rho_B) \leq H_2(F_{\text{bare}}),$$

where $H_2(x) = -x \log_2 x - (1-x) \log_2 (1-x)$ is the binary entropy.
**Equality holds** if and only if $\rho_B$ is diagonal in the logical basis.

*Proof sketch.* Writing $\rho_B$ as a $2 \times 2$ matrix in the logical basis
with off-diagonal element $c$, the entropy satisfies $S(\rho_B) \leq H_2(F_{\text{bare}})$
for all $|c|$, with equality at $|c| = 0$. ∎

### 2.4 Theorem 1 — The No-Go Theorem (Model-Independent, Archimedean)

**If** $F_{\text{bare}} > H_2^{-1}[(1-\delta)\ln 2]$, **then no environment
fragment can satisfy the Darwinism criterion.** Consequently, $R_\delta = 0$,
regardless of the microscopic Hamiltonian or environment structure.

**Proof chain** (all inequalities become equalities in the solvable model):

$$(1-\delta)\ln 2 \leq \chi(F) \leq \chi(E) \leq S(\rho_E) = S(\rho_B) \leq H_2(F_{\text{bare}}).$$

- $\chi(F) \geq (1-\delta)\ln 2$ — Darwinism criterion assumed for contradiction
- $\chi(F) \leq \chi(E)$ — monotonicity of Holevo information
- $\chi(E) \leq S(\rho_E)$ — Holevo bound
- $S(\rho_E) = S(\rho_B)$ — purification property for pure $|\Psi\rangle_{BE}$
- $S(\rho_B) \leq H_2(F_{\text{bare}})$ — Lemma 1
- Since $H_2$ is monotone decreasing on $[1/2, 1]$:
  **$F_{\text{bare}} \leq H_2^{-1}[(1-\delta)\ln 2]$**

Contradiction with the hypothesis. ∎

### 2.5 Corollary — Imperfect Recovery

For the imperfect-recovery model, the no-go threshold becomes:

$$F_L(N) > \eta + (1-\eta) \cdot H_2^{-1}[(1-\delta)\ln 2] \quad \Longrightarrow \quad R_\delta = 0.$$

**Operational example:** For $\delta = 0.10$ and $\eta = 0.60$, the threshold is

$$F_L(N) > 0.874 \quad \Longrightarrow \quad \text{zero Darwinistic redundancy}.$$

Any logical qubit protected with fidelity exceeding 87.4% produces ZERO redundant
classical records — the qubit is quantum-coherent but classically invisible.

### 2.6 Exact Tradeoff (Solvable Model Saturation)

In the exactly solvable limit $g_X = 0$, the solvable model saturates every
inequality in the proof chain:

$$\chi(E) = S(\rho_E) = S(\rho_B) = H_2(F_{\text{bare}}).$$

Every bit of logical entropy generated in the block is converted into **accessible
classical information** in the environment. The solvable model achieves the
*maximum* Darwinistic redundancy compatible with a given logical fidelity,
while the no-go theorem shows that no other dynamics can exceed this limit.

**Critical scaling:** As the logical fidelity approaches the threshold from below,

$$R_\delta \sim -\ln\big(F_L(N) - F_c\big) \quad \text{as} \quad F_L(N) \to F_c^+,$$

where $F_c = \eta + (1-\eta) \cdot H_2^{-1}[(1-\delta)\ln 2]$. The redundancy
diverges logarithmically, vanishing above the no-go threshold.

### 2.7 The Archimedean Shadow

The entire framework — Hamming distance, additive collective coupling, Shannon
entropy $H_2$, trace-distance fidelity, tensor-product environment — assumes
the Archimedean place. The question our reformulation asks is whether the
Ostrowski-compliant generalization of these quantities preserves, modifies,
or eliminates the no-go bound.

---

## 3. Ultrametric Code Spaces

> *[To be written — draws on Continuum Trilogy Paper I, Adelic Shannon Theory,
> and the Bruhat-Tits tree formalism from the CWI poster project.]*

### 3.1 The Bruhat-Tits Tree as an Information Geometry

The $p$-adic numbers $\mathbb{Q}_p$ have a natural tree structure: the Bruhat-Tits
tree $\mathcal{T}_p$ is an infinite $(p+1)$-regular tree whose vertices correspond
to $p$-adic balls. The distance between any two points satisfies the strong triangle
inequality.

### 3.2 Sphere Packings and Code Distances

In an ultrametric space, the strong triangle inequality forces spheres of the same
radius to be either identical or disjoint. This has direct consequences for the
geometry of error-correcting codes:

- The minimum distance between codewords is either an integer power of $p$ or infinite
  (there is no "between")
- The packing density on $\mathcal{T}_p$ has different asymptotic bounds than on
  Euclidean/Hamming spaces
- The concept of a "neighborhood" of a codeword (the set of correctable errors) is a
  $p$-adic ball, not an Archimedean sphere

### 3.3 Ostrowski's Theorem and the Dimensionless Mandate

Per the Ostrowski Dimensionless Mandate (QNFO Core §0.7): all physics formulas must
be expressed in dimensionless natural numbers, so they do not presume which completion
of $\mathbb{Q}$ is being used. The Maity et al. tradeoff relation — written in terms
of Archimedean fidelities and redundancies — is an Archimedean projection of a
potentially more general relation. The ultrametric reformulation makes this explicit.

---

## 4. The Tradeoff Under Ultrametric Transformation

> *[To be written — core derivation. This is the paper's main contribution.]*

### 4.1 Redundancy Redefined

In an ultrametric, the strong triangle inequality implies that for any three
environment fragments $e_1, e_2, e_3$:

$$d(e_1, e_3) \leq \max(d(e_1, e_2), d(e_2, e_3))$$

with equality of the two larger distances. This means that if fragments $e_1$ and
$e_2$ are within distance $r$ of a reference fragment $e_0$, then $e_1$ and $e_2$
are also within distance $r$ of each other. The notion of a "cluster" of similar
fragments — the operational definition of redundancy — becomes binary: either all
fragments in a cluster are mutually similar, or they are all mutually distant.
There is no intermediate regime of "partial" redundancy.

This suggests that the effective redundancy $R_U(f)$ in an ultrametric may be
**quantized** — taking only integer multiples of some fundamental redundancy quantum
tied to the $p$-adic valuation — rather than the continuous function $R(f)$ that
appears in the Archimedean tradeoff.

### 4.2 The Transformed Tradeoff

[To be derived. Key conjecture:]

$$R_U(f) \cdot F_L \leq C_U$$

where $C_U$ may differ from the Archimedean $C$, potentially admitting regimes where
both high logical fidelity and high redundancy coexist — or, conversely, where the
constraint is even tighter.

### 4.3 Falsifiable Predictions

1. **Prediction P1:** If the physical noise model in a QEC experiment has a
   significant $p$-adic (ultrametric) component, the observed tradeoff between
   logical fidelity and classical redundancy should deviate from the Archimedean
   prediction of Maity et al.
2. **Prediction P2:** The Archimedean tradeoff is a limiting case of a more general
   Ostrowski-compliant relation that reduces to the Maity et al. bound when
   evaluated at the Archimedean place.
3. **Disconfirmation condition:** If an experiment measures $R(f)$ and $F_L$ and
   finds agreement with the Archimedean bound at all physically accessible noise
   scales, then either (a) ultrametric effects are negligible at those scales, or
   (b) the no-go theorem is Ostrowski-invariant — both outcomes constrain the
   Continuum Trilogy's physical content.

---

## 5. Implications

> *[To be written.]*

### 5.1 If the Tradeoff Changes: A New Regime for QEC

### 5.2 If the Tradeoff Is Ostrowski-Invariant: A Deep Null Result

### 5.3 Connection to CWI QEC Workshop (Aug 24–28, 2026)

The poster presented at CWI asks: "What falsifies the QEC roadmap?" One possible
answer — explored in this paper — is that the roadmap assumes Archimedean code
geometry. If the physical noise in real quantum processors has an ultrametric
component (e.g., from 1/f noise with power-law spectra, or from non-Markovian
environments with hierarchical structure), then the ultimate bounds on QEC
performance may be different from current estimates.

---

## 6. Conclusion

> *[To be written.]*

---

## Declarations

### Competing Interests
None.

### Data Availability
All derivations are in the paper. The Shor [[9,1,3]] code is a standard QEC construction.

### Funding
This research received no specific grant from any funding agency.

### Pre-Registration
This paper's core predictions (§4.3, P1–P2) are timestamped by the git commit
history of the repository QNFO/qec-darwinism-ultrametric. The first commit
pre-registering these predictions is `[COMMIT_HASH]`.

---

## References (Preliminary)

- Maity, Onggadinata, Koh. *Exact Tradeoff Between Quantum Error Correction and
  Quantum Darwinism.* arXiv:2608.03944v1 (2026).
- Quni-Gudzinas, R. B. *Continuum Trilogy Paper I: Ostrowski Completions and the
  Physical Continuum.* Zenodo. DOI: 10.5281/zenodo.21672990.
- Quni-Gudzinas, R. B. *Adelic Shannon Theory.* Zenodo. DOI: 10.5281/zenodo.21698976.
- Quni-Gudzinas, R. B. *Five Pillars, One Framework: A Cross-Domain Audit.* Zenodo.
- [Additional references to be added during literature search — see PROJECT-PLAN.md §P2.]
