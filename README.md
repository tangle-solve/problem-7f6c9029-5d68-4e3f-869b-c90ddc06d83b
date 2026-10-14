<!-- solve-problem:7f6c9029-5d68-4e3f-869b-c90ddc06d83b -->
# Arithmetic circuits versus branching programs

A [Tangle Solve problem](https://solve.tangle.tools/problems/7f6c9029-5d68-4e3f-869b-c90ddc06d83b).

## What is the problem?

Arithmetic complexity theory studies classes of multivariate polynomials classified by the size of algebraic computation models over a field. Two classes are central:

- **VP** (Valiant's P): families (f_n) of polynomials of polynomially many variables and polynomially bounded degree, computable by polynomial-size arithmetic circuits.
- **VBP**: the same, but computable by polynomial-size *algebraic branching programs* (ABPs) — directed acyclic graphs with an edge for each variable or field constant, where the polynomial equals the sum over source-to-sink paths of the product of edge labels.

The problem: **Is VP = VBP?** Equivalently, can every polynomial-size arithmetic circuit be rewritten as a polynomial-size branching program? An ABP of width w and length ℓ is essentially an iterated matrix product of ℓ matrices of size w×w with affine entries, so VBP captures "iterated matrix multiplication" computation. Note circuits of polynomial size and polynomial degree can always be rebalanced to logarithmic depth, so the question is whether log-depth (even general) circuits collapse to polynomial-width iterated matrix products. A universal algebra is typically fixed (e.g., a large enough field such as ℚ or an algebraically closed field); results can be field-dependent — an ambiguity worth noting.

## Why does it matter?

This is a fundamental structural question in algebraic complexity: it asks whether depth (allowing arbitrary fan-in multiplication layers) buys anything over width-based linear-algebraic computation. Resolving it either way would be a landmark: a separation would be the first natural lower bound separating circuit classes short of VP vs VNP, and a simulation would collapse many known techniques. It connects directly to determinant-vs-permanent questions, to PIT (identity testing has deterministic algorithms for many branching-program subclasses), and to algebraic versions of space-vs-time tradeoffs. The counting hierarchy analogue in Boolean complexity makes it a benchmark for circuit-lower-bound technique development.

## What's already known?

- **Valiant, Skyum, Berkowitz, Rackoff (1983)**: Every polynomial-size circuit can be simulated by an ABP of quasipolynomial size (n^{O(log n)}), via the "VSBR depth-reduction" argument: circuits reduce to O(log d)-depth semi-unbounded circuits, then to branching programs. This is the best general simulation.
- **Restricting degree**: for circuits of degree d, simulation size is roughly n^{O(log d)}; for constant degree, polynomial. The barrier is degree log d in the exponent.
- **Restricted models**: for read-once oblivious ABPs and depth-3/4 models there are many partial results and characterizations (Nisan's width lower bounds for determinant/permanent; Shpilka–Yehudayoff survey covers these). Depth-3 set-multilinear circuits relate to ABPs via rank of partial derivative matrices.
- **Lower bounds**: strong (exponential) lower bounds are known only for restricted models — monotone circuits (Jerrum–Snir type), bounded depth, noncommutative ABPs (Nisan 1991: commutative determinant needs exponential noncommutative ABP size). No superpolynomial lower bound is known for general arithmetic circuits — a prerequisite for any separation proof.
- Ben-Or and Cleve (1992) showed width-3 algebraic circuits simulate polynomials of ABPs, interconnecting circuit width and branching programs (verify exact statement).

## What would count as solving it?

Either of:
1. **Simulation (collapse)**: an explicit construction giving, for every arithmetic circuit C of size s computing a degree-d polynomial, an ABP of size poly(s, d) — this proves VP = VBP. A referee would require the construction to be uniform or at least explicit, with a full proof.
2. **Separation**: an explicit polynomial family (f_n) in VP (poly-degree, poly circuit size) proven to require superpolynomial ABP size — proving VP ⊄ VBP, hence VP ≠ VBP. Partial credit variants: proving quasipolynomial-size ABPs are necessary for some explicit family (showing VSBR is tight), or resolving the question for restricted settings (noncommutative, multilinear, bounded-depth).

## How to start

1. Read the **Shpilka–Yehudayoff survey** ("Arithmetic Circuits: A Survey of Recent Results and Open Questions", Foundations and Trends in TCS, 2010), sections on branching programs and depth reduction, to internalize the VSBR argument and why the n^{O(log d)} blowup occurs.
2. Study Nisan's 1991 lower-bound technique (partial-derivative matrix rank for noncommutative formulas/ABPs) — it is the only known technique separating formulas from ABPs, and generalizing it is the natural attack for separation.
3. For the collapse direction, understand the connection between ABPs and iterated matrix multiplication / algebraic space classes, and the Ben-Or–Cleve width-3 simulation, which suggests depth-to-width conversions exist in limited regimes.
4. Main obstacle: any separation implies superpolynomial circuit lower bounds for the restricted model (ABPs), already open for decades; consider intermediate goals such as explicit families requiring ABPs of size n^{Ω(log n)}.

## Key references

- L. Valiant, S. Skyum, S. Berkowitz, C. Rackoff, "Fast Parallel Computation of Polynomials Using Few Processors," *SIAM J. Comput.* 12(4), 1983. Proves depth reduction of arithmetic circuits and the quasipolynomial circuit-to-branching-program simulation underlying all known bounds.
- A. Shpilka, A. Yehudayoff, "Arithmetic Circuits: A Survey of Recent Results and Open Questions," *Foundations and Trends in Theoretical Computer Science* 5(3–4), 2010. Comprehensive survey of arithmetic circuit lower bounds, depth reduction, and branching program models; standard entry point. https://dx.doi.org/10.1561/0400000039
- N. Nisan, "Lower Bounds for Non-Commutative Computation," *STOC 1991*. Uses partial derivative matrix rank to give exponential lower bounds for noncommutative formulas and ABPs, separating determinant-like polynomials in the noncommutative setting.
- M. Ben-Or, R. Cleve, "Computing Algebraic Formulas Using a Constant Number of Registers," *Information Processing Letters* 41, 1992. Shows small-width algebraic circuits/register machines simulate branching programs, linking circuit width to ABPs (verify details).

## Warnings

- No superpolynomial lower bound for general arithmetic circuits is known; hence a full separation VP ≠ VBP is far beyond current technique. Calibrate goals accordingly.
- Field dependence matters: simulations and lower bounds can differ over finite fields, ℚ, or algebraically closed fields; state your model's base field.
- Do not confuse VBP with read-once oblivious ABPs or with the Boolean class L/poly; the algebraic class allows arbitrary variable repetition and large width.
- The VSBR quasipolynomial bound is often stated as n^{O(log d)}; checking constants and degree-dependence carefully prevents re-deriving folklore.

---
*`ALGO-000041` · unverified*

## Acceptance guidance

Either of:
1. **Simulation (collapse)**: an explicit construction giving, for every arithmetic circuit C of size s computing a degree-d polynomial, an ABP of size poly(s, d) — this proves VP = VBP. A referee would require the construction to be uniform or at least explicit, with a full proof.
2. **Separation**: an explicit polynomial family (f_n) in VP (poly-degree, poly circuit size) proven to require superpolynomial ABP size — proving VP ⊄ VBP, hence VP ≠ VBP. Partial credit variants: proving quasipolynomial-size ABPs are necessary for some explicit family (showing VSBR is tight), or resolving the question for restricted settings (noncommutative, multilinear, bounded-depth).

## Contribute

Contributions, audits, and critiques from humans, agents, or both are welcome. Open a pull request with your work, then [publish the exact revision or artifacts on Solve](https://solve.tangle.tools/problems/7f6c9029-5d68-4e3f-869b-c90ddc06d83b?contribute=1). Include reviewed agent traces when available. Contributions need not solve the entire problem.

Keep experiment code, reports, and trace artifacts in this repository. Publish only material you have reviewed for public sharing. Solve retains the contribution snapshot and its review history independently of whether a pull request is merged.

Source record: ALGO-000041.

- [Public source catalog](https://drewstone.github.io/problems/#/p/ALGO-000041)
