# PHYS 2300 – Quantum Computing: Complete Lecture Notes

---

## Week 1 (Week1_2026.pdf)

**Content:** Almost entirely images/diagrams (no extractable text).  
**Reference link included in slides:** Bloch sphere interactive simulation:  
https://www.st-andrews.ac.uk/physics/quvis/simulations_html5/sims/blochsphere/blochsphere.html

---

## Lecture 2 — Linear Operators (Sections 2.1.2–2.1.4)

### Linear Operators — Definitions

- A **linear operator** A: V → W satisfies: A(Σ aᵢ|vᵢ⟩) = Σ aᵢ A|vᵢ⟩
- **Identity operator** Iᵥ|v⟩ = |v⟩ for all |v⟩ ∈ V
- **Zero operator** 0|v⟩ = 0 for all |v⟩ ∈ V
- **Composition** of operators: if A: V→W and B: W→X, then BA: V→X

### Matrix Representation

- For basis sets {|v⟩ᵢ} in V and {|w⟩ⱼ} in W:  
  A|v⟩ᵢ = Σⱼ Aⱼᵢ |w⟩ⱼ  
  → standard matrix multiplication: **b⃗ = A · a⃗**
- Matrix of composite operator C = BA:  
  Cₖᵢ = Σⱼ BₖⱼAⱼᵢ

### Outer Product Representation

- For |v⟩ ∈ V and |w⟩ ∈ W: operator A = |w⟩⟨v| acts as A|ψ⟩ = ⟨v|ψ⟩|w⟩
- **Completeness relation:** I = Σᵢ |i⟩⟨i| for any orthonormal basis {|i⟩}

### Pauli Matrices and Single-Qubit Gates — MEMORIZE

| Gate | Matrix |
|------|--------|
| I (Identity) | [[1,0],[0,1]] |
| X (NOT / bit flip) | [[0,1],[1,0]] |
| Y | [[0,−i],[i,0]] |
| Z (phase flip) | [[1,0],[0,−1]] |
| H (Hadamard) | (1/√2)[[1,1],[1,−1]] |
| P(γ) (Phase) | [[e^{−iγ/2},0],[0,e^{iγ/2}]] |

### Key Actions

- X|0⟩ = |1⟩, X|1⟩ = |0⟩  (bit flip / logical NOT)
- H|0⟩ = |+⟩ = (|0⟩+|1⟩)/√2,  H|1⟩ = |−⟩  (basis change)
- Z = |0⟩⟨0| − |1⟩⟨1|,  H = (1/√2)(|0⟩⟨0| + |1⟩⟨0| + |0⟩⟨1| − |1⟩⟨1|)

### Important Identities

- X² = Y² = Z² = H² = I
- XY = iZ,  YX = −iZ  → gates are **non-commutative**

### Cauchy-Schwartz Inequality

|⟨v|w⟩|² ≤ ⟨v|v⟩⟨w|w⟩

---

## Lecture 3 — Eigenvalues, Eigenvectors, Operator Functions (Sections 2.1.5–2.1.9)

### Eigenvalues and Eigenvectors

- A|v⟩ = λ|v⟩; eigenvalues found from **characteristic equation** det|A − λI| = 0
- A is **diagonalizable** iff it has a diagonal (outer product) representation: A = Σᵢ λᵢ|i⟩⟨i|

### Example: Pauli Y Diagonalization

- Eigenvalues: {−1, +1}  
- Eigenvectors: |v₁⟩ = (1/√2)[i,1]ᵀ (spin along −y),  |v₂⟩ = (1/√2)[−i,1]ᵀ (spin along +y)
- Y = −|v₁⟩⟨v₁| + |v₂⟩⟨v₂|

### Non-diagonalizable Example

- A = [[1,0],[1,1]] → only one eigenvector: cannot form a basis in C²

### Adjoint Operator

- A⁺ ≡ (Aᵀ)* (conjugate transpose)
- (A⁺)⁺ = A,  (AB)⁺ = B⁺A⁺
- Outer product: (a|i⟩⟨i|)⁺ = a*|i⟩⟨i|

### Hermitian Operators

- A is **Hermitian** (self-adjoint) if A⁺ = A → all eigenvalues are real
- **Projector** on subspace W = span{|1⟩,…,|k⟩}: P = Σᵢ₌₁ᵏ |i⟩⟨i|
  - P is Hermitian, **P² = P** (idempotent)
  - Physical meaning: once you measure a state, repeated identical measurements give the same result

### Normal Operators & Spectral Decomposition

- A is **normal** if AA⁺ = A⁺A
- **Spectral decomposition theorem:** A is normal ↔ A is diagonalizable
- **Unitary operators** U: UU⁺ = U⁺U = I → normal, diagonalizable, preserves inner products

### Positive Operators

- A is **positive** if ⟨v|A|v⟩ ≥ 0 for all |v⟩
- If A is positive → all eigenvalues λᵢ ≥ 0

### Operator Functions

- For Hermitian A = Σᵢ λᵢ|i⟩⟨i|: f(A) ≡ Σᵢ f(λᵢ)|i⟩⟨i|
- Key result: **e^{iθv⃗·σ⃗} = cos(θ)I + i sin(θ)(v⃗·σ⃗)**  (where |v⃗|=1)
- Pauli algebra: σᵢσⱼ = δᵢⱼI + iΣₖ εᵢⱼₖσₖ, {σᵢ,σⱼ} = 2δᵢⱼI

### Trace

- tr(A) = Σᵢ Aᵢᵢ
- tr(AB) = tr(BA),  tr(I) = 2,  tr(σᵢ) = 0
- Trace is **invariant** under unitary similarity: tr(UAU⁺) = tr(A)

### Commutator / Anti-commutator

- [A,B] = AB − BA;  {A,B} = AB + BA
- [σᵢ,σⱼ] = 2i Σₖ εᵢⱼₖσₖ;  {σᵢ,σⱼ} = 2δᵢⱼI
- **Theorem:** [A,B] = 0 ↔ A and B are simultaneously diagonalizable → simultaneously measurable quantities

---

## Lecture 4 — Tensor Products and Multi-Qubit States (Sections 1.3.2, 1.3.4–1.3.6, 2.1.7)

### Tensor Products

- For Hilbert spaces V (dim n) and W (dim m): V⊗W has dim = nm
- 2-qubit space: |vw⟩ = (α₁|0⟩+β₁|1⟩)⊗(α₂|0⟩+β₂|1⟩) ∈ V⊗V ≡ V⊗²
- Computational basis (order matters!): {|00⟩, |01⟩, |10⟩, |11⟩}

### Tensor Product Rules

- z(|v⟩⊗|w⟩) = (z|v⟩)⊗|w⟩ = |v⟩⊗(z|w⟩)
- (A⊗B)|v⟩⊗|w⟩ = (A|v⟩)⊗(B|w⟩)
- Matrix rep via **Kronecker product**: A⊗B = block matrix [aᵢⱼB]
- Inner product: ⟨ij|i′j′⟩ = ⟨i|i′⟩·⟨j|j′⟩ = δᵢᵢ′·δⱼⱼ′

### Example — X⊗Y

Result is a 4×4 matrix with off-diagonal entries ±i

### CNOT Gate

- UCN|c⟩|t⟩ = |c⟩|t⊕c⟩
- Matrix representation (computational basis |00⟩,|01⟩,|10⟩,|11⟩):  
  UCN = [[1,0,0,0],[0,1,0,0],[0,0,0,1],[0,0,1,0]]

### Bell States (Entangled 2-qubit)

- Created by H⊗I followed by CNOT (or UCN · (H⊗I))
- |β₀₀⟩ = (|00⟩+|11⟩)/√2

---

## Lecture 5 — Quantum Algorithms (Sections 1.3.7, 1.4.1–1.4.4)

### Classical Computations on a Quantum Computer

- Classical gates: NOT, AND, OR, XOR, NAND, NOR
- Only NOT is reversible; all quantum gates must be reversible (they are unitaries)
- **Toffoli gate T** (3-qubit): {a,b,c} → {a,b,c⊕ab} — T⁻¹ = T
  - T(a,b,1) = (a,b,a NAND b) → Toffoli can simulate any classical computation
  - T is a valid quantum gate; quantum T **cannot copy** an unknown quantum state (**no-cloning theorem**)

### Quantum Teleportation

**Setup:**
- Alice (qubit 1) and Bob (qubit 2) share Bell state |β₀₀⟩ = (|00⟩+|11⟩)/√2
- Alice also holds unknown state |ψ⟩ = α|0⟩+β|1⟩

**Circuit (4 steps):**
1. Alice applies CNOT (with her |ψ⟩ as control, her entangled qubit as target)
2. Alice applies Hadamard to |ψ⟩ qubit
3. Alice measures her two qubits (result M₁M₂ ∈ {00,01,10,11}, each with prob 1/4)
4. Alice calls Bob; Bob applies Z^{M₁}·X^{M₂} to recover |ψ⟩

**Notes:**
- Does NOT violate special relativity (classical communication required)
- Does NOT violate no-cloning (Alice no longer has |ψ⟩ after teleportation)

### Deutsch–Jozsa Algorithm

**Problem:** f(x): {0,…,2ⁿ−1} → {0,1}, either constant or balanced. Determine which.  
- Classical: 2ⁿ/2 + 1 evaluations needed  
- Quantum: **1 evaluation**

**Oracle Uf:** |xy⟩ → |x⟩⊗|y⊕f(x)⟩

**Algorithm:**  
1. Start: |0⟩⊗ⁿ|1⟩  
2. Apply H⊗ⁿ⊗H → (1/√2ⁿ)Σₓ|x⟩ ⊗ (|0⟩−|1⟩)/√2  
3. Apply Uf → Σₓ(−1)^{f(x)}|x⟩/√2ⁿ ⊗ |−⟩  
4. Apply H⊗ⁿ → Σₓ,z(−1)^{[x·z]+f(x)}|z⟩/2ⁿ ⊗ |−⟩  
5. Measure first n qubits:
   - If all zeros → f is constant
   - If any nonzero → f is balanced

**Key identity:** H⊗ⁿ|x⟩ = Σz (−1)^{[x·z]}|z⟩/√2ⁿ

**General comments:**
- Exponentially faster than classical (impractical application though)
- Real-world quantum algorithms need **quantum error correction**
- Shor's algorithm (factoring) and Grover's search are practical examples

---

## Lecture 6 — Postulates of Quantum Mechanics (Section 2.2)

### Postulate I — State Space

- Every isolated system has a **Hilbert space** (complex inner product vector space)
- The system's state is a **unit state vector** |ψ⟩ with ⟨ψ|ψ⟩ = 1
- Example: qubit → Hilbert space C², |ψ⟩ = α|0⟩+β|1⟩, |α|²+|β|² = 1

### Postulate II — Evolution

- Evolution of a closed system described by **unitary operator U**: |ψ⟩′ = U|ψ⟩
- U can depend on time: U = U(t₂,t₁), UU⁺ = I

### Postulate II' — Schrödinger Equation (continuous time)

- iℏ d|ψ⟩/dt = H|ψ⟩ (ℏ = Planck's constant, set to 1 in QC)
- H is Hermitian (**Hamiltonian**)
- Corresponding unitary: U(t,t₁) = e^{−iH(t−t₁)/ℏ}
- Energy eigenstates: H|E⟩ = E|E⟩;  time dependence: |E⟩(t) = e^{−iE(t−t₀)/ℏ}|E⟩₀
- Any unitary can be written as U = e^{iK} with K Hermitian

### Postulate III — Quantum Measurements

- Described by collection {Mₘ} (m = measurement outcome)
- Probability: p(m) = ⟨ψ|Mₘ⁺Mₘ|ψ⟩
- Post-measurement state: |m⟩ = Mₘ|ψ⟩/√p(m)
- **Completeness:** Σₘ Mₘ⁺Mₘ = I

**Example — Computational basis measurement:**
- M₀ = |0⟩⟨0|, M₁ = |1⟩⟨1|
- p(0) = |α|², p(1) = |β|²

### Distinguishability

- **Orthogonal states CAN be distinguished** (with certainty): construct Mᵢ = |ψᵢ⟩⟨ψᵢ|
- **Non-orthogonal states CANNOT be distinguished** with certainty (proof by contradiction)

### Projective Measurements

- Measurement operators are projectors: Pₘ² = Pₘ, Pₘ⁺ = Pₘ
- **Observable:** M = Σₘ m·Pₘ
- **Expectation value:** E(M) = ⟨M⟩ = ⟨ψ|M|ψ⟩
- **Standard deviation:** [ΔM]² = ⟨M²⟩ − ⟨M⟩²

### Heisenberg Uncertainty Principle

For any two Hermitian operators C, D and any state |ψ⟩:  
**Δ(C)·Δ(D) ≥ (1/2)|⟨ψ|[C,D]|ψ⟩|**

Example: C=X, D=Y, ψ=|0⟩ → Δ(X)·Δ(Y) = 1·1 ≥ 1 ✓

### POVM Measurements

- Set of operators {Eₘ} where each Eₘ ≥ 0 (positive) and Σₘ Eₘ = I
- **Useful when we only care about probabilities**, not post-measurement state
- Can distinguish states "sometimes, never wrong" — e.g., |0⟩ vs |+⟩

### Postulate IV — Composite Systems

- Hilbert space of composite system = **tensor product** of component spaces
- **Entanglement:** composite system can be in a state not writable as tensor product
- Bell state |β₀₀⟩ = (|00⟩+|11⟩)/√2 is entangled
- Entanglement is why quantum computers are more powerful

---

## Lecture 7 — Density Operator (Section 2.4)

### Definition

- System in ensemble {|ψᵢ⟩, pᵢ}: **density operator** ρ = Σᵢ pᵢ|ψᵢ⟩⟨ψᵢ|

### Properties

- **Trace condition:** tr(ρ) = 1
- **Positivity:** ⟨φ|ρ|φ⟩ ≥ 0 for all |φ⟩
- Conversely: any positive trace-1 operator is a valid density matrix

### Evolution & Measurement

- Under unitary U: ρ → ρ′ = UρU⁺
- Probability of outcome m: p(m) = tr(Mₘ⁺Mₘ ρ)
- Post-measurement state: ρₘ = Mₘ ρ Mₘ⁺ / tr(Mₘ⁺Mₘ ρ)
- If measurement record lost: ρ′ = Σₘ Mₘ ρ Mₘ⁺

### Pure vs Mixed States

- **Pure state:** ρ = |ψ⟩⟨ψ|, tr(ρ²) = 1
- **Mixed state:** tr(ρ²) < 1
- **Maximally mixed state:** ρ = I/d (no information)

### Non-uniqueness of Ensemble

- Different ensembles {pᵢ, |ψᵢ⟩} and {λᵢ, |φᵢ⟩} give same ρ if connected by unitary: √pᵢ|ψᵢ⟩ = Σⱼ uᵢⱼ √λⱼ|φⱼ⟩
- Probabilities have no unique physical meaning

### Reduced Density Operator

- Composite system AB, only A observable:  
  **ρᴬ = trB(ρᴬᴮ)** (partial trace over B)
- For product state ρᴬᴮ = ρ⊗σ:  ρᴬ = ρ,  ρᴮ = σ
- For Bell state |β₀₀⟩: ρ₁ = I/2 (maximally mixed!)

### Quantum Teleportation — What Bob Knows Before Alice Calls

- Bob's reduced density matrix before Alice's call: **ρ_Bob = I/2**
- Bob has **zero information** about |ψ⟩ — no faster-than-light signaling

### General Single-Qubit Density Matrix

ρ = (I + r⃗·σ⃗)/2,   |r⃗| ≤ 1  (Bloch ball)

- |r⃗| = 1 → **pure state** (surface of Bloch sphere)
- |r⃗| < 1 → **mixed state** (interior of Bloch ball)

---

## Lecture 8 — EPR and Bell Inequality (Section 2.6)

### Setup (Bell's Experiment)

- Charlie prepares two particles; Alice measures Q or R (outcomes ±1); Bob measures S or T (outcomes ±1)
- Measurements are **causally disconnected** (different continents)
- They compute correlations: E(QS), E(RS), E(RT), E(QT)

### Bell Inequality (Classical / Local Realism)

From QS+RS+RT−QT = (Q+R)S+(R−Q)T, classical reasoning implies:  
**(Q+R)S+(R−Q)T = ±2**  
→ **Bell inequality:** E(QS) + E(RS) + E(RT) − E(QT) ≤ 2

### Quantum Mechanics Violation

- Charlie prepares: |ψ⟩ = (|01⟩−|10⟩)/√2
- Alice: Q=Z₁, R=X₁; Bob: S=(−Z₂−X₂)/√2, T=(Z₂−X₂)/√2
- All measurements have eigenvalues ±1

**QM computes:**
- E(QS) = E(RS) = E(RT) = 1/√2,  E(QT) = −1/√2
- **E(QS)+E(RS)+E(RT)−E(QT) = 2√2 ≈ 2.83 > 2** → Bell inequality ***violated***!

### Conclusion

- Experiments confirm QM prediction (Aspect, Clauser, Zeilinger — 2022 Nobel Prize relevance)
- **Local realism is wrong**: physical properties do not have definite pre-existing values independent of observation
- Nobody has found a way to modify QM postulates and still reproduce experiment
- For further reading: **ER=EPR** (deep connections to quantum gravity)

---

## Lecture 9 — Elements of Quantum Circuits (Sections 4.2–4.4)

### Big Picture: Universal Quantum Computing

To achieve universality:
1. Any n-qubit unitary → product of **two-level unitaries**
2. Any two-level unitary → **single-qubit gates + CNOT**
3. Any single-qubit gate → approximated by **H and T** (to arbitrary precision)

→ **Universal gate set:** {H, T, CNOT}

### Single-Qubit Operations — Bloch Sphere

- State |ψ⟩ = a|0⟩+b|1⟩ ↔ unit vector n⃗ on Bloch sphere (θ,φ)
- Opposite vectors on Bloch sphere → orthogonal states: ⟨χ|ψ⟩ = 0
- Unitary 2×2 matrix: 4 free real parameters

### Gate Identities

- H = (X+Z)/√2,  S = T²,  Z = S²
- S ~ Rz(π/2),  T ~ Rz(π/4)  (up to global phase)

### Rotation Operators

- Rₓ(θ) = e^{−iθX/2} = cos(θ/2)I − i·sin(θ/2)X
- R_y(θ) = e^{−iθY/2} = cos(θ/2)I − i·sin(θ/2)Y
- Rz(θ) = e^{−iθZ/2} = diag(e^{−iθ/2}, e^{iθ/2})

### Decomposition Theorems

- **Theorem I:** U = e^{iα}·Rₙ(θ) for some unit vector n⃗ and angle θ
- **Theorem II (Z-Y decomposition):** U = e^{iα}·Rz(β)·R_y(γ)·Rz(δ)
- **Theorem III:** Any two fixed non-parallel unit vectors m̂, n̂ →  U = e^{iα}·Rₙ(β)·Rₘ(γ)·Rₙ(δ)

**Key consequence:** For any single-qubit gate U, there exist A, B, C (unitaries) with:  
ABC = I  and  U = e^{iα}·A·X·B·X·C

### Controlled Operations

- **CNOT:** |c⟩|t⟩ → |c⟩|t⊕c⟩ (target flipped when control = 1)
- **Controlled-U:** |c⟩|t⟩ → |c⟩Uᶜ|t⟩
- Control and target bits can be flipped: H⊗²·UCN·H⊗² implements reversed CNOT

### Cₙ(U) Gates (n-control-qubit U)

- C₁(U): any single qubit gate, circuit uses A, X, B, X, C decomposition
- C₂(U): uses √U such that V² = U
- **Toffoli gate** = C₂(X): realized exactly with {H,S,T,CNOT}
- Cₙ(U) generalized circuit: uses n−1 ancilla qubits, each Toffoli gate used twice (ancilla returned to |0⟩)

### Measurement Principles

- **Principle of deferred measurement:** intermediate measurements can always be moved to end of circuit
- **Principle of implicit measurement:** unterminated quantum wires are assumed to be measured

---

## Lecture 10 — Universal Quantum Gates (Sections 4.5.1–4.5.4)

### Universal Gate Sets

- Classical: Toffoli gate is universal
- Quantum: Any n-qubit unitary U (2ⁿ×2ⁿ) can be **exactly decomposed** as product of ≤ 2^{n-1}(2ⁿ−1) **two-level unitaries**
- Two-level unitaries → single-qubit gates + CNOT
- Single-qubit gates → approximated by {H, T} to any precision

### Two-Level Unitaries Are Universal (Proof Sketch)

For d×d unitary U, construct U₁,…,U_{d-1} that zero out the first column:
- Needs d(d−1)/2 two-level unitaries total
- For n qubits: d = 2ⁿ → needs 2^{n-1}(2ⁿ−1) unitaries

### Single-Qubit + CNOT Gates Are Universal

- Decompose any two-level unitary using **Gray code** connecting binary strings s and t
- Each Gray code step = controlled-CNOT operation
- Apply controlled-Ũ at the middle, then undo Gray code steps in reverse
- Each step = product of single-qubit gates and CNOT

### Approximating Single-Qubit Gates with {H, T}

- Want to approximate any U to precision ε: E(U,V) = max||ψ|| ||(U−V)|ψ⟩|| < ε
- Key rotation constructed from T and H:  
  - T = e^{iπ/8}·Rz(π/4),  HTH = e^{iπ/8}·Rₓ(π/4)
  - e^{−iπ/4}·T·HTH = Rₙ(θ) for **irrational** θ/2π
- **Pigeonhole principle:** for small δ, N = ⌈2π/δ⌉+1 angle values θₖ = kθ (mod 2π) must have two within δ of each other → can approximate rotation by arbitrarily small angle → can approximate rotation by any angle

---

## Lecture 11 — Quantum Fourier Transform and Phase Estimation (Sections 5.1, 5.2)

### Context: Shor's Algorithm Complexity

- Classical (number field sieve): ~exp(n^{1/3} ln^{2/3} n) operations
- Shor's quantum: ~n² ln n ln ln n operations

### Classical DFT

- {x₀,…,x_{N-1}} → {y₀,…,y_{N-1}}:  yₖ = (1/√N) Σⱼ xⱼ e^{2πijk/N}
- Inverse: xₙ = (1/√N) Σₖ yₖ e^{−2πink/N}

### Quantum Fourier Transform (qFT)

- |j⟩ → (1/√N) Σₖ e^{2πijk/N}|k⟩
- Unitary: (U_qFT)_{αβ} = (1/√N) e^{2πi(α−1)(β−1)/N}

### Product Representation (Key Theorem)

For N = 2ⁿ and j = j₁j₂…jₙ (binary):

**qFT|j⟩ = (|0⟩+e^{2πi·0.jₙ}|1⟩)·(|0⟩+e^{2πi·0.j_{n-1}jₙ}|1⟩)···(|0⟩+e^{2πi·0.j₁j₂…jₙ}|1⟩) / 2^{n/2}**

where 0.jₗjₗ₊₁…jₘ = jₗ/2¹ + jₗ₊₁/2² + … + jₘ/2^{m−ℓ+1}

### qFT Circuit

- Uses gates Rₖ = [[1,0],[0,e^{2πi/2ᵏ}]] where R₁=Z, R₂=S, R₃=T
- For each qubit |jₗ⟩: apply H then controlled-Rₖ gates
- Add final swap operations to reverse qubit order
- Circuit depth: O(n²)

### Phase Estimation Algorithm

**Task:** Given unitary U with eigenvector |u⟩ (U|u⟩ = e^{2πiφ}|u⟩), estimate φ to precision 2^{−t}

**Algorithm:**
1. Initialize t-qubit register as |0⟩⊗ᵗ, second register as |u⟩
2. Apply H to each qubit in first register
3. Apply controlled-U^{2ʲ} operations for j=0,1,…,t−1
4. Result: qFT|φ₁…φₜ⟩⊗|u⟩
5. Apply inverse qFT to first register
6. Measure first register → obtain φ̃ within 2^{−t} of φ

---

## Lecture 12 — The Quantum Search Algorithm (Section 6.1)

### Grover's Algorithm — Overview

**Problem:** Search unstructured database of N = 2ⁿ items for M solutions.  
- Classical: ~N/M evaluations  
- Grover's quantum: ~√(N/M) evaluations

### Oracle

- f(x) = 1 if x is a solution, 0 otherwise
- Oracle operation: |x⟩|q⟩ → |x⟩|q⊕f(x)⟩
- With |q⟩ = |−⟩: **O|x⟩ = (−1)^{f(x)}|x⟩** (phase kickback)

### Algorithm Steps

1. Prepare equal superposition: |ψ⟩ = H⊗ⁿ|0⟩⊗ⁿ = (1/√N)Σₓ|x⟩
2. Apply Grover operator G exactly R = CI[π/4 · √(N/M)] times
3. Measure: obtain a solution x* with error probability ~ M/N ≪ 1

### Grover Operator G

G = (2|ψ⟩⟨ψ| − Iₙ) · O

- O reflects about the subspace of non-solutions |α⟩
- (2|ψ⟩⟨ψ|−Iₙ) reflects about |ψ⟩

### Geometric Interpretation

Define:
- |α⟩ = equal superposition of non-solutions
- |β⟩ = equal superposition of solutions, ⟨α|β⟩ = 0
- |ψ⟩ = √((N−M)/N)|α⟩ + √(M/N)|β⟩ = cos(θ/2)|α⟩ + sin(θ/2)|β⟩

Each application of G rotates the state by angle θ toward |β⟩:  
Gᵏ|ψ⟩ = cos((2k+1)θ/2)|α⟩ + sin((2k+1)θ/2)|β⟩

**Number of iterations:** R = CI[arccos(√(M/N)) / θ]  
When M ≪ N: R ≈ CI[π/4 · √(N/M)]

**Probability of error:** sin²γ ≤ (θ/2)² ~ M/N ≪ 1

### Quadratic Speedup Summary

| Problem | Classical | Quantum |
|---------|-----------|---------|
| Unstructured search N items | O(N) | O(√N) |
| Factoring n-bit integer | exp(n^{1/3}) | O(n² log n) |
| Deutsch-Jozsa (constant vs balanced) | 2^{n-1}+1 | 1 |
| qFT | O(n·2ⁿ) classical DFT | O(n²) |

---

## Key Notation Reference

| Symbol | Meaning |
|--------|---------|
| \|ψ⟩ | Ket (state vector) |
| ⟨ψ\| | Bra (dual vector) |
| ⟨φ\|ψ⟩ | Inner product |
| \|φ⟩⟨ψ\| | Outer product (operator) |
| A⁺ | Adjoint (conjugate transpose) |
| ⊗ | Tensor product |
| \|0⟩, \|1⟩ | Computational basis states |
| \|+⟩, \|−⟩ | Hadamard basis: (|0⟩±|1⟩)/√2 |
| \|β₀₀⟩ | Bell state (|00⟩+|11⟩)/√2 |
| ρ | Density matrix |
| trB(ρ) | Partial trace over subsystem B |
| CI(x) | Closest integer to x |
| [x·z] | Bitwise inner product mod 2 |
