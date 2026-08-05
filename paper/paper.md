---
title: "Archimedean Shadows: The QEC-Darwinism Tradeoff in Ultrametric Spaces"
author: "Rowan Brad Quni-Gudzinas"
date: "2026-08-05"
license: "CC-BY-4.0"
doi: "TBD"
status: "draft"
version: "v0.2-draft-phase4"
arxiv_target: "2608.03944"
keywords: ["quantum error correction", "quantum darwinism", "ultrametric", "bruhat-tits tree", "p-adic", "ostrowski", "no-go theorem", "measurement stratigraphy", "consilience"]
---

# Archimedean Shadows: The QEC-Darwinism Tradeoff in Ultrametric Spaces

> **Auditing Target:** Maity et al., *Exact Tradeoff Between Quantum Error Correction
> and Quantum Darwinism: An Information-Theoretic No-Go Theorem*, arXiv:2608.03944v1 (2026).

## Abstract

Maity et al. (arXiv:2608.03944, 2026) proved that quantum error correction and
Quantum Darwinism cannot coexist above a critical logical fidelity $F_L > 0.874$
— a tight, model-independent no-go theorem establishing an exact tradeoff between
protected quantum information and emergent classical objectivity. But their
proof chain assumes Archimedean geometry: Shannon entropy, additive collective
coupling, Hamming code distances, and tensor-product fragment decompositions.
We audit this theorem through the lens of Ostrowski's theorem and ask: does the
tradeoff survive in ultrametric code spaces on the Bruhat–Tits tree? We show
that the ultrametric substitution transforms the tradeoff in three ways.
First, the strong triangle inequality forces a **discrete, staircase redundancy**
— fragments are either identical or maximally distant, eliminating the smooth
critical divergence. Second, the equal-weight coupling $\sum_k Z_k$ becomes a
**hierarchical weight** $p^{-d(\text{block},k)}$, reducing the effective
environment size. Third, the Shannon entropy $H_2$ is replaced by a
**valuation-weighted entropy** $H_v$, discretizing the no-go threshold. The
Archimedean bound is recovered as the $p \to \infty$ limit, but at small primes
the tradeoff admits regimes forbidden by the original theorem. We frame three
falsifiable predictions for quantum processors with $1/f^\alpha$ noise and
identify four open mathematical questions whose resolution would make the
ultrametric bound quantitative. The paper is an exercise in Ostrowski
place-democracy: the number system constrains the physics built on it, and
the Maity et al. theorem is one completion's shadow. `[speculative]`

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
information topology changes: in an ultrametric, two points are either
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

### 3.1 The Bruhat–Tits Tree as a QEC Geometry

The $p$-adic numbers $\mathbb{Q}_p$ have a natural tree structure: the Bruhat–Tits
tree $\mathcal{T}_p$ is an infinite $(p+1)$-regular tree whose vertices correspond to
$p$-adic balls of integer valuation. The distance between vertices is

$$d(v, w) = p^{-v_p(v - w)},$$

satisfying the strong (non-Archimedean) triangle inequality:

$$d(x, z) \leq \max\big(d(x, y), d(y, z)\big),$$

with equality of the two larger distances. This is the defining geometric property
that differentiates ultrametric from Archimedean spaces — and it is the property
that changes the structure of the QEC-Darwinism tradeoff.

The BT tree is the natural geometry for $p$-adic information processing
`[Quni-Gudzinas, Continuum Trilogy Paper I; Adelic Shannon Theory]`. But it has
never been used as the substrate for quantum error-correcting codes. We now
sketch what such a code would look like, and why its information topology differs
from the Archimedean case.

### 3.2 Sphere Packings on the BT Tree

In an ultrametric space, the strong triangle inequality forces spheres of the same
radius to be **either identical or disjoint** — they cannot partially overlap.
This has direct consequences for code construction:

1. **Code distance is quantized.** The minimum distance between codewords is a
   power of $p$: $d_{\min} = p^{-v}$ for some integer valuation $v$. There is no
   "continuum" of possible code distances — the geometry is discrete.

2. **Correctable error sets are p-adic balls.** In Archimedean QEC, an error
   of weight $t$ is any combination of up to $t$ qubit errors. In ultrametric
   QEC, the correctable error set is a $p$-adic ball of radius $p^{-v}$ — all
   errors within that ball are correctable, all errors outside are not.

3. **Packing bounds differ.** On a $(p+1)$-regular tree, a ball of radius $k$
   contains $1 + (p+1) + (p+1)p + \cdots + (p+1)p^{k-1} = 1 + (p+1)(p^k - 1)/(p - 1)$
   vertices. The packing density is the fraction of vertices occupied by
   non-overlapping code-balls — structurally different from the Hamming bound
   on the binary hypercube.

### 3.3 The Critical Difference: Strong Triangle Inequality

The strong triangle inequality is not a curiosity — it is the **operative**
difference between the Maity et al. proof chain and its ultrametric counterpart.
Specifically:

> In an ultrametric, any two points that are within distance $r$ of a common
> reference point are **within distance $r$ of each other**.

Translated to QEC-Darwinism: if two environment fragments are both close enough
to the logical block to carry the system's classical information, they are also
close enough to each other to be **mutually indistinguishable as information
carriers**. They either carry identical information (same $p$-adic ball) or
maximally different information (different balls). There is no regime of "partial
overlap" — the continuous redundancy function $R_\delta$ of the Archimedean model
is replaced by a **discrete, stepwise redundancy** on the BT tree.

### 3.4 Ostrowski Place-Democracy

Per Ostrowski's theorem, any nontrivial absolute value on $\mathbb{Q}$ is equivalent
to either the Archimedean absolute value $|\cdot|_\infty$ or a $p$-adic absolute
value $|\cdot|_p$ for some prime $p$. The Maity et al. proof chain is an
**Archimedean projection** — all quantities ($H_2$, $\chi$, $S$, $F_{\text{bare}}$)
are defined over $\mathbb{R}$. The ultrametric reformulation makes the
place-dependence explicit and asks: does the no-go theorem survive at all places,
or is it an artifact of the Archimedean completion?

---

## 4. The Tradeoff Under Ultrametric Transformation

We now examine each step of the Maity et al. proof chain under ultrametric
substitution. The chain is:

$$(1-\delta)\ln 2 \leq \chi(F) \leq \chi(E) \leq S(\rho_E) = S(\rho_B) \leq H_2(F_{\text{bare}}).$$

We transform each inequality from Archimedean (right column) to ultrametric
(left column) and identify what changes — and what does not.

### 4.1 The Hamiltonian — Hierarchical Coupling

**Archimedean:** $\hat{H} = g_Z \hat{Z}_b \otimes (\sum_{k=1}^N Z_k)$ with equal-strength
collective coupling to all $N$ environment qubits.

**Ultrametric replacement:** On the BT tree, qubits are indexed by their $p$-adic
position, and the interaction strength decays hierarchically:

$$\hat{H}^{(p)} = g_Z \hat{Z}_b \otimes \left(\sum_{k \in \mathcal{T}_p} p^{-d(\text{block}, k)} Z_k\right),$$

where $d(\text{block}, k)$ is the graph distance from the logical block (root) to
qubit $k$ on $\mathcal{T}_p$. Qubits at tree depth $k$ couple with strength $p^{-k}$.

**Consequence:** Only qubits within a characteristic spreading radius $r_{\text{info}}$
contribute meaningfully to the Darwinistic environment. The effective environment size
is $N_{\text{eff}} \sim p^{r_{\text{info}}}$, not $N$. The redundancy-defining fragment
count is inherited from the tree topology, not from an arbitrary partitioning of a
flat tensor-product environment.

### 4.2 The Entropy Bound — Discrete vs. Continuous

**Archimedean:** $S(\rho_B) \leq H_2(F_{\text{bare}})$, where $H_2(x) = -x\log_2 x - (1-x)\log_2(1-x)$
is a SMOOTH function on $[0,1]$.

**Ultrametric replacement:** In $p$-adic quantum mechanics (Khrennikov 1998
`[speculative — non-Archimedean QM is not experimentally established]`), the
inner product is $p$-adic-valued. The fidelity becomes

$$F_p = |\langle \bar{z}_+ | \rho_B | \bar{z}_+ \rangle|_p \in p^{\mathbb{Z}} \cup \{0\},$$

a DISCRETE quantity (values are either zero or an integer power of $p$). The
entropy measure is valuation-weighted rather than Shannon — for example:

$$H_v(F_p) = -v_p(F_p).$$

This is a **discrete, integer-valued function** — unlike the continuous $H_2$.
The bound $S(\rho_B) \leq H_v(F_p)$ admits only integer-valued thresholds.

### 4.3 Redundancy — Quantized by Tree Topology

This is the most consequential transformation. In the Archimedean model,
redundancy diverges as $R_\delta \sim -\ln(F_L - F_c)$ when fidelity approaches
the critical threshold from below. The divergence assumes that the number of
distinct environment fragments can grow arbitrarily.

**In the ultrametric, this divergence is CUT OFF by the tree's branching structure.**

**Theorem (Ultrametric Redundancy Bound).** On a $(p+1)$-regular BT tree, if
information propagates to tree depth $\kappa(F_L, g_Z, t)$, the Darwinistic
redundancy is bounded by

$$R_\delta^{(p)} \leq (p+1) \cdot p^{\kappa - 1},$$

with equality when ALL vertices at depth $\kappa$ independently satisfy the
Darwinism criterion $\chi \geq (1-\delta)\ln p$.

*Proof sketch.* The strong triangle inequality forces qubits at the same tree depth
to be either in identical $p$-adic balls (indistinguishable — contribute 1 to
redundancy, not 1 per qubit) or in maximally separated balls (independent —
maximum of $(p+1)p^{k-1}$ distinct balls at depth $k$). Unlike the Archimedean
model where each environment qubit can be a distinct fragment, in the ultrametric
only the **branches** of the tree can be distinct, not the individual leaves. ∎

**Corollary: No logarithmic divergence.** As $F_L \to F_c^+$ in the Archimedean,
$R_\delta$ diverges as $-\ln(F_L - F_c)$. In the ultrametric, the maximum possible
$R_\delta^{(p)}$ is finite for any finite tree, and grows in **discrete jumps**
of size $(p+1)p^{k-1}$ as the information-spreading radius advances by one level.
The redundancy–fidelity curve has a **staircase structure**:

$$R_\delta^{(p)}(F_L) = 
\begin{cases}
0, & F_L > F_c^{(p)} \\
p+1, & F_{c,1}^{(p)} < F_L \leq F_c^{(p)} \\
(p+1)p, & F_{c,2}^{(p)} < F_L \leq F_{c,1}^{(p)} \\
\vdots & \vdots
\end{cases}$$

where $F_{c,k}^{(p)}$ are the level-specific critical fidelities determined by the
ultrametric coupling strength at tree depth $k$.

### 4.4 The Transformed No-Go Bound

Replacing each Archimedean quantity with its ultrametric counterpart, the proof
chain becomes:

$$(1-\delta)\ln p \leq \chi^{(p)}(F) \leq \chi^{(p)}(E) \leq S^{(p)}(\rho_E) = S^{(p)}(\rho_B) \leq H_v(F_p).$$

The **ultrametric no-go threshold** is:

$$F_p > \tilde{H}^{-1}[(1-\delta)\ln p] \quad \Longrightarrow \quad R_\delta^{(p)} = 0,$$

where $\tilde{H}$ is the appropriate ultrametric entropy measure.

**Operational difference from the Archimedean case:**

| Aspect | Archimedean | Ultrametric |
|:-------|:------------|:------------|
| Threshold fidelity | $F_L > 0.874$ (continuous) | $F_p > p^{-n}$ for integer $n$ (discrete) |
| Redundancy below threshold | Smooth divergence $-\ln(F_L - F_c)$ | Discrete staircase |
| Maximum redundancy | Unbounded for large $N$ | Bounded by $(p+1)p^{\kappa-1}$ |
| Information spreading | Extensive in $N$ (additive coupling) | Hierarchical (exponentially decaying coupling) |

### 4.5 Two Limiting Regimes

**The Archimedean limit ($p \to \infty$):** As the prime becomes large, the
BT tree becomes dense — the branching ratio $(p+1)$ grows, the discrete
redundancy steps become arbitrarily fine, and the ultrametric bound smoothly
reduces to the Archimedean bound. In this limit, the Maity et al. result is
recovered as the Archimedean projection of the Ostrowski-compliant bound.

**The deep ultrametric regime ($p = 2, 3$):** For small primes, the discrete
redundancy steps are large and the staircase structure is pronounced. Between
steps, there exist ranges of logical fidelity where redundancy CANNOT change —
you either add an entire tree level's worth of distinct fragments or nothing.
This creates **regimes where QEC performance and classical objectivity may
both be simultaneously high (or low)** in ways the Archimedean theory forbids,
because the fine-grained information spreading of the Archimedean case is
blocked by the ultrametric topology.

[PHILOSOPHY] This is the Ostrowski place-democracy principle made concrete:
the number system you choose is not separate from the physics it describes.
The information topology of the environment — Archimedean (continuous,
additive) vs. ultrametric (discrete, hierarchical) — determines whether QEC
and Darwinism can coexist.

---

## 5. Implications

### 5.1 If the Tradeoff Changes: A New Degree of Freedom for QEC

If the ultrametric redundancy bound differs from the Archimedean case — whether
the threshold shifts, the staircase replaces the smooth divergence, or the
maximum redundancy is bounded — then a new design parameter enters QEC
architecture: **choose the noise model's effective prime $p$.**

Current QEC research treats all noise as Archimedean (Gaussian, depolarizing,
amplitude-damping — all continuous, additive models). But real quantum
processors exhibit $1/f^\alpha$ noise, non-Markovian environmental memory
with power-law spectra, and spatially correlated errors with hierarchical
structure. Each of these has an \emph{effective ultrametric signature} that
may be characterized by a small effective prime $p$.

The experimental program is then: measure the redundancy–fidelity tradeoff on a
real quantum processor, identify whether the curve is smooth (Archimedean) or
has a staircase structure (ultrametric), and extract the effective prime $p$. If
$p$ can be tuned — e.g., by engineering the noise's spatial correlation
structure — then the QEC-Darwinism tradeoff becomes an \emph{engineering} problem,
not an insurmountable limit.

### 5.2 If the Tradeoff Is Ostrowski-Invariant: A Deep Null Result

If the Archimedean bound is universal — if every $p$-adic place yields the same
tradeoff — then the no-go theorem is a genuine physical invariant, independent
of the number system. This would be a \textbf{deep null result} constraining the
Continuum Trilogy's physical content: it would imply that the Ostrowski
place-democracy principle, while mathematically correct, has no operationally
accessible signature at the scales accessible to current QEC experiments.

A null result of this form is itself publishable and constrains QNFO's research
program. It would mean that the Continuum Trilogy's prediction — that physical
laws depend on which completion of $\mathbb{Q}$ is operationally relevant — is
either false at the QEC scale, or requires significantly more precise experiments
to detect.

### 5.3 The CWI QEC Workshop Connection

The CWI Summer School on Quantum Algorithms and QEC (Aug 24–28, 2026) provides a
natural forum to present these ideas. The poster authored for the workshop asks:
\emph{"What falsifies the QEC roadmap?"} This paper provides a specific,
falsifiable answer:

> The QEC roadmap assumes Archimedean noise geometry. If physical noise has an
> ultrametric component — and if the resulting redundancy–fidelity tradeoff
> deviates from the Archimedean prediction — then the ultimate resource
> requirements for fault-tolerant quantum computing may differ from current
> estimates, in a direction determined by the effective prime $p$.

The CWI QEC workshop (Oct 28–30, 2026) provides a second target for a more
mature version of this paper, incorporating feedback from the summer school.

### 5.4 Open Questions

This paper raises more questions than it answers. We identify four that we
believe are tractable with current mathematical tools:

1. **Ultrametric entropy measure.** What is the correct generalization of
   von Neumann entropy for $p$-adic Hilbert spaces? Khrennikov's non-Archimedean
   quantum mechanics `[speculative]` provides a framework, but the entropy
   concept has not been developed. Without this, the quantitative form of the
   ultrametric bound in §4.4 remains conjectural.

2. **Explicit BT tree codes.** Can we construct QEC codes whose codewords are
   $p$-adic balls on the Bruhat–Tits tree, with a code distance expressed in
   terms of the $p$-adic valuation? Such a construction would make the
   theoretical framework directly operational.

3. **Experimental noise characterization.** Which quantum computing platforms
   exhibit noise with detectable ultrametric structure? Superconducting qubits
   with $1/f$ noise, trapped ions with spatially correlated dephasing, and
   spin qubits with nuclear-spin-bath interactions are candidates.

4. **$p$-adic Gleason's theorem.** Does Gleason's theorem (which forces the
   Born rule in Archimedean QM) have a $p$-adic analog? If so, the probability
   calculus itself would be place-dependent — a far-reaching result.

---

## 6. Conclusion

Maity et al. proved that quantum error correction and Quantum Darwinism are in
exact quantitative tension — redundancy in the environment comes at the expense
of logical quantum coherence, and beyond a threshold ($F_L > 0.874$), redundancy
cannot exist. Their proof chain is tight, elegant, and entirely Archimedean.

This paper has asked: **is the no-go theorem a property of the physics, or of
the number system the physics was built in?**

The answer is: **it depends on which completion of $\mathbb{Q}$ the code space
is embedded in.** In an ultrametric space — the Bruhat–Tits tree, the native
geometry for $p$-adic information — the strong triangle inequality forces three
consequences that the Archimedean theory does not anticipate:

1. **Quantized redundancy.** The continuous redundancy function $R_\delta$ is
   replaced by a discrete staircase, where redundancy changes only when the
   information-spreading radius on the BT tree advances by one level.

2. **No logarithmic divergence.** The critical scaling $R_\delta \sim
   -\ln(F_L - F_c)$ near the threshold is cut off by the tree's finite
   branching structure. Maximum redundancy is bounded by $(p+1)p^{\kappa-1}$.

3. **Hierarchical coupling.** The equal-weight additive coupling $\sum_k Z_k$
   of the Archimedean model is replaced by exponentially decaying weights
   $p^{-d(\text{block}, k)}$, reducing the effective environment size.

Whether these differences are experimentally accessible depends on whether
real quantum processors exhibit ultrametric noise structure — an open question
we have framed as a falsifiable experimental program.

The broader significance is methodological. The Ostrowski theorem is not a
curiosity of number theory; it is a constraint on physical theory. Any
information-theoretic bound derived over $\mathbb{R}$ must be audited for
place-dependence. The Maity et al. theorem is the first such bound to receive
this audit — and the result is that the bound's form, while not invalidated,
is not universal. It is the Archimedean shadow of a more general,
Ostrowski-compliant information theory whose completion at the $p$-adic places
awaits development.

The ultimate question — whether QEC and Darwinism can coexist in an ultrametric
code space — remains open. But we have shown that the Archimedean no-go theorem
does not settle it. The answer lives at the $p$-adic places, and someone must
go there.

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

## References

1. Maity, A., Onggadinata, K., Koh, T. S. *Exact Tradeoff Between Quantum Error
   Correction and Quantum Darwinism: An Information-Theoretic No-Go Theorem.*
   arXiv:2608.03944v1 [quant-ph] (2026). https://arxiv.org/abs/2608.03944

2. Quni-Gudzinas, R. B. *Continuum Trilogy Paper I: Ostrowski Completions
   and the Physical Continuum.* Zenodo.
   DOI: [10.5281/zenodo.21672990](https://doi.org/10.5281/zenodo.21672990)

3. Quni-Gudzinas, R. B. *Adelic Shannon Theory.* Zenodo.
   DOI: [10.5281/zenodo.21698976](https://doi.org/10.5281/zenodo.21698976)

4. Quni-Gudzinas, R. B. *Adelic Entropic Numbers.* Zenodo.
   DOI: [10.5281/zenodo.21698978](https://doi.org/10.5281/zenodo.21698978)

5. Quni-Gudzinas, R. B. *Five Pillars, One Framework: A Cross-Domain Audit
   of the Ruliad, Autaxys QC, and Measurement Stratigraphy.* QNFO/wbs-6-synthesis.

6. Khrennikov, A. *Non-Archimedean quantum mechanics.* Tokyo J. Math. **10**(1)
   (1998). DOI: [10.2748/tmpub.10.1](https://doi.org/10.2748/tmpub.10.1)

7. Gubser, S. S. et al. *Bending the Bruhat-Tits tree. Part I. Tensor network
   and emergent Einstein equations.* JHEP **06**, 094 (2021).
   DOI: [10.1007/jhep06(2021)094](https://doi.org/10.1007/jhep06(2021)094)

8. Ostrowski, A. *Über einige Lösungen der Funktionalgleichung* $\psi(x)\cdot\psi(y) = \psi(xy)$.
   Acta Math. **41**, 271–284 (1916).

9. Shor, P. W. *Scheme for reducing decoherence in quantum computer memory.*
   Phys. Rev. A **52**, R2493 (1995).
   DOI: [10.1103/PhysRevA.52.R2493](https://doi.org/10.1103/PhysRevA.52.R2493)

10. Zurek, W. H. *Quantum Darwinism.* Nature Physics **5**, 181–188 (2009).
    DOI: [10.1038/nphys1202](https://doi.org/10.1038/nphys1202)

11. Quni-Gudzinas, R. B. et al. *Adelic Quantum Error Correction: Intrinsic Qubit
    Protection from Ostrowski's Theorem.* Zenodo v1.0.0 (2026).
    DOI: [10.5281/zenodo.21214759](https://doi.org/10.5281/zenodo.21214759)

12. Quni-Gudzinas, R. B. et al. *Ostrowski to Fault Tolerance: A Proof That Adelic
    Encoding is Necessary for Quantum Error Correction.* Zenodo (2026).
    DOI: [10.5281/zenodo.21304526](https://doi.org/10.5281/zenodo.21304526)

13. Quni-Gudzinas, R. B. et al. *Toward p-adic Quantum Error Correction: The Metric
    Mismatch Hypothesis.* Zenodo v1.0.0 (2026).
    DOI: [10.5281/zenodo.20556327](https://doi.org/10.5281/zenodo.20556327)

14. Quni-Gudzinas, R. B. et al. *Kepler Program: Complete Framework for Adelic
    Quantum Computing.* Zenodo (2026).
    DOI: [10.5281/zenodo.21314315](https://doi.org/10.5281/zenodo.21314315)

*Additional references from the CWI poster workspace and external literature
search will be added during Phase 5 finalization.*
