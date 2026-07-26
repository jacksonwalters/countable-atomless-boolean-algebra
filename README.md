# Countable Atomless Boolean Algebra

A Lean 4 formalization of the cylinder-set construction underlying the
countable atomless Boolean algebra, also known as the Cantor algebra.

The construction begins with Cantor space, represented as the type of infinite
Boolean sequences `ℕ → Bool`. A finite bitstring determines a cylinder set:
the set of all infinite sequences having that bitstring as a prefix. Finite
unions of cylinder sets form a Boolean subalgebra of the power set of Cantor
space.

For mathematical motivation and a paper proof of the construction, see
[Construction of the Cantor Algebra](https://jacksonwalters.com/docs/notes/construction_countable_atomless_boolean_algebra.pdf).

## Formalized results

The development:

- defines finite bitstrings, Cantor space, cylinder sets, and compatibility;
- proves that incompatible cylinders have empty intersection;
- proves that compatible cylinders intersect in another cylinder;
- expresses complements and intersections of finite unions of cylinders as
  finite unions of cylinders;
- constructs `CountableAtomlessBA` as a `BooleanSubalgebra (Set Cantor)`;
- proves that every cylinder splits into two disjoint, nonempty cylinders; and
- proves that every nonempty element of `CountableAtomlessBA` contains a
  nonempty proper subelement.

The main theorem is:

```lean
theorem CountableAtomlessBA_is_atomless :
  ∀ b ∈ CountableAtomlessBA.carrier, b.Nonempty →
  ∃ a ∈ CountableAtomlessBA.carrier, a.Nonempty ∧ a ⊂ b
```

The formalization currently establishes the Boolean-algebra construction and
its atomlessness. Countability and uniqueness up to Boolean-algebra
isomorphism are not formalized here.

## Building

The project uses Lean 4.26.0 and mathlib 4.26.0. With
[elan](https://github.com/leanprover/elan) installed, the committed toolchain
and Lake manifest select the required versions automatically:

```sh
git clone https://github.com/jacksonwalters/countable-atomless-boolean-algebra.git
cd countable-atomless-boolean-algebra
lake build
```

## Project structure

- [`AtomlessBooleanAlgebra/Basic.lean`](AtomlessBooleanAlgebra/Basic.lean)
  contains the construction and proofs.
- [`AtomlessBooleanAlgebra.lean`](AtomlessBooleanAlgebra.lean) is the library
  entry point.

## Citation

Citation metadata is provided in [`CITATION.cff`](CITATION.cff). GitHub's
**Cite this repository** menu can export the citation in common formats.

## License

This project is released under the [MIT License](LICENSE).
