# TEST-NEEDS — k9_ex

<!-- SPDX-License-Identifier: MPL-2.0 -->
<!-- (PMPL-1.0-or-later preferred; MPL-2.0 required for Hex.pm) -->

## CRG C — Test Coverage Achieved

CRG C gate requires: unit, smoke, build, P2P (property-based), E2E,
reflexive, contract, aspect, and benchmark tests.

| Category      | File                        | Count | Notes                                      |
|---------------|-----------------------------|-------|--------------------------------------------|
| Unit          | `test/k9_test.exs`          | 9     | Parser, renderer, security levels          |
| Smoke         | `test/k9_test.exs`          | —     | Covered by minimal parse/render tests      |
| Build         | `mix compile`               | —     | CI gate                                    |
| Property/P2P  | `test/k9_property_test.exs` | 6     | Determinism, anti-symmetry, reflexivity    |
| E2E           | `test/k9_test.exs`          | 1     | Full component parse/render roundtrip      |
| Reflexive     | `test/k9_property_test.exs` | 1     | `compare(x,x) == :eq` for all levels      |
| Contract      | `test/k9_contract_test.exs` | 10    | Named invariants (error/ok guarantees)     |
| Aspect        | `test/k9_aspect_test.exs`   | 9     | Security, correctness, performance, resilience |
| Benchmark     | `test/k9_bench_test.exs`    | 4     | Timing guards (parse/render/roundtrip)     |

**Total: 43 tests, 0 failures**

## Running Tests

```bash
mix test
```

## Test Taxonomy (Testing Taxonomy v1.0)

- **Unit**: individual function correctness
- **Smoke**: essential path does not crash
- **Build**: compilation gate (mix compile)
- **Property/P2P**: determinism, algebraic laws, invariants over many inputs
- **E2E**: full parse → render → re-parse pipeline
- **Reflexive**: `compare(x,x) == :eq` identity laws
- **Contract**: named behavioural invariants (error-tuple guarantee, etc.)
- **Aspect**: cross-cutting concerns (security input safety, performance bounds, resilience)
- **Benchmark**: wall-clock regression guards
