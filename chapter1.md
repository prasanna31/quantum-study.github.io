# Chapter 1: Classical Computing Foundations

## 1.1 Classical Computing
Classical computing processes information using deterministic, macroscopic physical states (voltages in transistors) governed by classical physics. Every state is definite: a switch is on or off, never both. Built on the von Neumann architecture (CPU, memory, I/O, stored program), it executes instructions sequentially via a fetch-decode-execute cycle. Moore's Law-driven miniaturization made it ubiquitous, but it defines the baseline against which quantum computing is compared.

## 1.2 Computers, Computation and Information
- **Computation**: a systematic transformation of input into output by following rules (an algorithm).
- **Information** (Shannon): a measure of uncertainty resolved. A fair coin flip carries 1 bit; entropy is H = -Σ p·log₂(p).
- A computer is any physical system that can be set up, evolved by rules, and read out. The Church-Turing thesis states that every effectively computable function can be computed by a Turing machine, so all classical computers are equivalent in power (differing only in speed).

## 1.3 Classical Bits and Binary Representation
A **bit** is a variable that is exactly 0 or 1. Strings of bits encode everything:
- Integers: positional binary, e.g. 1011₂ = 8+2+1 = 11. Negatives use two's complement.
- Reals: IEEE 754 floating point (sign, exponent, mantissa).
- Text: ASCII/Unicode. Images/sound: sampled numeric arrays.
- n bits represent 2ⁿ distinct values, but only ONE at a time (contrast: a qubit register holds amplitudes over all 2ⁿ).
- Bits can be freely copied and read without disturbance, a property quantum states lack.

## 1.4 Logic Gates
Physical devices that implement elementary Boolean functions:
- **NOT** (inverts), **AND** (1 if both 1), **OR** (1 if any 1), **XOR** (1 if inputs differ)
- **NAND** and **NOR** are *universal*: any circuit can be built from one of them alone.
- Gates combine into adders, multiplexers, latches, registers, and ultimately CPUs.
- Most classical gates are **irreversible** (AND maps 4 inputs to 2 outputs, losing information). Landauer's principle: erasing a bit dissipates at least kT·ln2 of heat. Reversible gates (Toffoli, Fredkin) matter later because quantum gates must be reversible.

## 1.5 Boolean Logic
Algebra over {0,1} with operations ∧, ∨, ¬ (George Boole).
- Laws: commutativity, associativity, distributivity, identity, complement; **De Morgan**: ¬(A∧B) = ¬A ∨ ¬B.
- Any function can be written in sum-of-products (DNF) or product-of-sums (CNF) form, using a truth table.
- Simplification (Karnaugh maps, Quine-McCluskey) minimizes gate count.
- Satisfiability (SAT), deciding if a Boolean formula can be made true, is the canonical NP-complete problem.

## 1.6 Classical Algorithms
A finite, unambiguous, terminating procedure for solving a problem.
- Paradigms: divide and conquer (merge sort), dynamic programming, greedy, backtracking, randomized.
- Measured by time and space as functions of input size n using Big-O: O(log n) binary search, O(n log n) sorting, O(n²) naive multiplication, O(2ⁿ) brute-force search.
- Key examples later contrasted with quantum: search (O(n) classical vs Grover's O(√n)) and factoring (best classical is sub-exponential vs Shor's polynomial).

## 1.7 Mathematical Foundations
Tools underlying all of the above:
- **Sets, functions, relations**; **modular arithmetic** (basis of cryptography, e.g. RSA).
- **Proof techniques**: induction, contradiction, construction.
- **Complex numbers**: z = a+bi, |z|² = a²+b², Euler's formula e^{iθ} = cosθ + i sinθ. Not needed classically, but essential for quantum amplitudes.
- **Logarithms and exponentials** for growth rates; **graphs** and **combinatorics** for counting states.

## 1.8 Linear Algebra Fundamentals
The language of quantum mechanics, also used in classical ML and graphics.
- **Vectors** (lists of numbers), **matrices** (linear maps), operations: addition, scalar multiplication, dot product, matrix multiplication (non-commutative).
- **Inner product**: ⟨u|v⟩ measures overlap; norm ‖v‖ = √⟨v|v⟩.
- **Eigenvalues/eigenvectors**: Av = λv; the directions a matrix only stretches.
- **Special matrices**: Hermitian (A = A†, real eigenvalues, observables), unitary (U†U = I, preserve length, reversible evolution).
- **Tensor (Kronecker) product** ⊗: combines systems; dimension multiplies (2 bits → 4 states).
- Classical bit as vector: |0⟩ = [1,0]ᵀ, |1⟩ = [0,1]ᵀ; gates become matrices (NOT = [[0,1],[1,0]]).

## 1.9 Probability and Statistics
Handles uncertainty, randomness, and noisy measurement.
- **Probability**: P(A) in [0,1], sums to 1 over outcomes; conditional P(A|B) = P(A∧B)/P(B); **Bayes**: P(A|B) = P(B|A)P(A)/P(B).
- **Random variables**: expectation E[X] = Σ x·p(x), variance Var = E[X²] - E[X]².
- **Distributions**: Bernoulli, binomial, normal; law of large numbers lets repeated trials estimate probabilities.
- **Randomized algorithms** use coin flips for speed (bounded-error BPP).
- Classical probabilities are non-negative and add; quantum amplitudes can be negative/complex and **interfere**. That difference is the heart of quantum advantage.

## 1.10 Computation and Complexity
Classifies problems by resources needed as n grows.
- **P**: solvable in polynomial time (sorting). **NP**: solutions verifiable in polynomial time (SAT, factoring, TSP). **NP-complete**: hardest in NP. **PSPACE**, **EXP**: larger classes. **BPP**: efficient with randomness.
- P ⊆ NP ⊆ PSPACE ⊆ EXP; whether P = NP is open.
- **Reductions** show one problem is at least as hard as another.
- Quantum class **BQP** is believed to contain problems outside P (factoring) but probably not NP-complete ones.

## 1.11 Limitations of Classical Computing
- **Computability**: some problems are undecidable (the Halting Problem, Turing 1936), regardless of hardware.
- **Intractability**: exponential-time problems (NP-hard optimization, factoring-based cryptanalysis, simulating quantum systems) become infeasible; simulating n qubits needs 2ⁿ numbers.
- **Physical limits**: transistor scaling nears atomic size (~nm), leakage and heat (power wall), end of Moore's Law/Dennard scaling, Landauer heat bound.
- **Sequential bottleneck**: von Neumann memory-CPU bandwidth; parallelism helps only by constant/polynomial factors (Amdahl's law).
- **Motivation for quantum computing**: exploits superposition, entanglement, and interference to tackle certain problems (factoring, search, chemistry simulation) more efficiently, though it does not break computability limits.