# Chapter 1: Classical Computing, Explained Step by Step

**The logical chain of this chapter:**
Computers (1.1, 1.2) → store data as bits (1.3) → process bits with gates (1.4) → gates follow Boolean logic (1.5) → logic is organised into algorithms (1.6) → maths supports everything (1.7, 1.8, 1.9) → complexity measures how hard problems are (1.10) → limits show why we need something new (1.11).

---

## 1.1 Classical Computing
**What it is:** Computing based on classical physics, where every physical state is definite. A tubelight is either ON or OFF; it is never "both".

- Hardware: transistors acting as tiny switches (high voltage = 1, low voltage = 0).
- Design: the von Neumann architecture, i.e. CPU + memory + input/output, running a stored program one instruction at a time (fetch → decode → execute).
- **Why it matters:** Your laptop, phone and even a supercomputer are all classical. Quantum computing is always judged against this baseline.

## 1.2 Computers, Computation and Information
Three ideas, each building on the previous one:

1. **Information** is the answer to a question. Claude Shannon measured it as the reduction in uncertainty. A fair coin toss gives exactly 1 bit; formula: H = −Σ p·log₂(p).
2. **Computation** is converting input information into output information by following fixed rules (an algorithm), like a recipe.
3. **Computer** is any physical device that can hold information, change it by rules, and show the result.

**Church-Turing thesis:** Anything that can be computed at all can be computed by a Turing machine. Hence, all classical computers have the *same power*; they differ only in speed.

## 1.3 Classical Bits and Binary Representation
**Bit** = a variable that is exactly 0 or 1. This is the smallest unit of classical information.

- Why binary? Two voltage levels are easy to build and resistant to noise.
- Place values are powers of 2: 1011₂ = 8 + 0 + 2 + 1 = 11.
- Everything is encoded in bits: numbers (two's complement, IEEE 754), text (ASCII, Unicode), images (pixel values), audio (samples).
- n bits can represent 2ⁿ different values, **but only one value at a time**.
- Bits can be copied and read freely without disturbing them. (A qubit cannot be copied; remember this for later.)

## 1.4 Logic Gates
Having stored bits, we now need to *change* them. Gates are small circuits that do this.

| Gate | Rule |
|------|------|
| NOT  | Flips the bit |
| AND  | 1 only if both inputs are 1 |
| OR   | 1 if at least one input is 1 |
| XOR  | 1 if inputs are different |
| NAND / NOR | Universal: *any* circuit can be built using only NAND (or only NOR) |

- Gates → adders → registers → ALU → CPU. A processor is just billions of gates.
- **Irreversibility:** AND takes 2 bits and gives 1, so the inputs cannot be recovered. By Landauer's principle, erasing one bit releases at least kT·ln2 of heat. Reversible gates (Toffoli, Fredkin) avoid this, and quantum gates must be reversible.

## 1.5 Boolean Logic
Gates are the *hardware*; Boolean algebra is the *mathematics* behind them (George Boole). It works only with 0 and 1 using ∧ (AND), ∨ (OR), ¬ (NOT).

- Key laws: commutative, associative, distributive, and **De Morgan:** ¬(A∧B) = ¬A ∨ ¬B.
- Any truth table can be written as a formula (sum-of-products), hence any function can be built from gates.
- Simplifying formulae (Karnaugh maps) reduces gate count, saving cost and power.
- **SAT problem:** "Can this formula be made true?" It is the first proven NP-complete problem (links to 1.10).

## 1.6 Classical Algorithms
Circuits do small jobs; an **algorithm** is a finite, clear, terminating step-by-step method to solve a whole problem.

- Common approaches: divide and conquer (merge sort), greedy, dynamic programming, backtracking, randomised methods.
- We judge an algorithm by how its time/memory grows with input size n, using Big-O:
  - O(log n) binary search → very fast
  - O(n log n) good sorting
  - O(n²) simple multiplication
  - O(2ⁿ) brute force → becomes impossible quickly
- Benchmarks for quantum comparison: *unstructured search* takes O(n) classically versus O(√n) with Grover; *factoring* is sub-exponential classically versus polynomial with Shor.

## 1.7 Mathematical Foundations
The basic toolkit needed before going further:

- **Sets, functions, relations** for describing problems precisely.
- **Modular arithmetic** (clock arithmetic), the base of RSA encryption.
- **Proof techniques:** induction, contradiction, construction.
- **Logarithms and exponentials** to understand growth rates.
- **Complex numbers:** z = a + bi; Euler's formula e^(iθ) = cosθ + i·sinθ. Unused in classical computing but central to quantum amplitudes.

## 1.8 Linear Algebra Fundamentals
Why now? Because bits, gates and (later) qubits can all be written as vectors and matrices.

- **Vector:** a list of numbers; **matrix:** a rule that transforms vectors. Matrix multiplication is *not* commutative (AB ≠ BA in general).
- **Inner product** ⟨u|v⟩ measures how much two vectors overlap; norm = √⟨v|v⟩ is the length.
- **Eigenvector:** Av = λv. The matrix only stretches it, never rotates it.
- **Hermitian matrix** (A = A†): real eigenvalues, represents measurable quantities. **Unitary matrix** (U†U = I): preserves length, so it is reversible.
- **Tensor product (⊗):** joins systems together; sizes multiply (2 bits → 4 states).
- **Worked example:** |0⟩ = [1, 0]ᵀ, |1⟩ = [0, 1]ᵀ, and NOT gate = [[0,1],[1,0]]. Multiply NOT with |0⟩ and you get |1⟩.

## 1.9 Probability and Statistics
Real-world data is noisy and many algorithms use randomness, so we need a way to handle uncertainty.

- Probabilities lie between 0 and 1 and sum to 1 over all outcomes.
- **Conditional probability:** P(A|B) = P(A∧B)/P(B). **Bayes' rule:** P(A|B) = P(B|A)·P(A)/P(B).
- **Expectation:** E[X] = Σ x·p(x). **Variance:** E[X²] − (E[X])².
- Common distributions: Bernoulli, binomial, normal. Law of large numbers: more trials give a better estimate.
- **Key contrast for later:** Classical probabilities are never negative and only add up. Quantum amplitudes can be negative or complex and can *cancel* each other (interference). This is the source of quantum advantage.

## 1.10 Computation and Complexity
Now that we can write algorithms, we ask: *how hard is a problem itself?*

- **P:** solvable quickly (polynomial time), e.g. sorting.
- **NP:** answer can be *checked* quickly, e.g. SAT, factoring, travelling salesman.
- **NP-complete:** the hardest problems in NP; solve one quickly and you solve all of them.
- **BPP:** solvable quickly with randomness. **PSPACE, EXP:** bigger classes.
- Order: P ⊆ NP ⊆ PSPACE ⊆ EXP. Whether P = NP is still an open question.
- **Reduction** = converting problem A into B to show B is at least as hard.
- Quantum class **BQP** probably contains problems outside P (like factoring) but likely not NP-complete problems.

## 1.11 Limitations of Classical Computing
Putting everything together, classical computers face four kinds of walls:

1. **Computability:** Some problems are impossible for *any* computer, e.g. the Halting Problem (Turing, 1936).
2. **Intractability:** Exponential-time problems (hard optimisation, breaking RSA by factoring, simulating molecules) become unmanageable. Simulating n qubits needs 2ⁿ numbers, so 300 qubits would need more numbers than atoms in the universe.
3. **Physical limits:** Transistors are approaching atomic size, heat and leakage are rising, and Moore's Law is slowing down.
4. **Sequential bottleneck:** Memory-CPU speed gap (von Neumann bottleneck); by Amdahl's law, parallelism gives only limited speed-up.

**Conclusion:** These limits motivate quantum computing, which uses superposition, entanglement and interference to handle *specific* problems (factoring, search, chemistry simulation) more efficiently. Note that it does **not** solve undecidable problems; it only changes what is *efficiently* solvable.