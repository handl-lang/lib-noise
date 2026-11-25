# lib-noise

Noise **port types** for the Handl platform — the contract side of the
port/impl split. Backends `noise-c` (perlin/simplex) and `noise-stub`
implement the same interface, selected by platform configuration.

## Layout

| path | role |
| --- | --- |
| `src/index.hnl` | the contract — `Noise` grade + op signatures |
| `pkg.hnl` | manifest — dep `type`, `modules: ["noise"]` |
| `scripts/hnl-gate.sh`, `ci.sh` | the gate / bupha entry |

## Contract

- Deterministic lattice-noise contract: coordinate-driven pseudo-random
  value generation; all backends are pure and carry the `Noise`
  grade.
- Surface: `Perlin1d`/`Perlin2d`/`Perlin3d`, `Simplex2d`/`Simplex3d`
  (`Number ~> Number` / `(Number, Number) ~> Number` / …).

## Verification

```bash
HNL=../host-cli/target/debug/hnl scripts/hnl-gate.sh
```

## License

MIT.

<!-- myco:agent-awareness -->

## Agent awareness

- Session start / any work discussion: run `myco status --prompt`
  before proposing next steps — know the board first.
- User describes new work → offer to capture it (`myco todo add`,
  `issue new`, `proposal new`). Don't wait to be asked.
- Picking up a task: `myco resume <ID>` is the briefing.
- Wrapping up: `myco handoff <ID>` anything resumable; keep statuses
  honest (claimed → in-progress → blocked/done).

<!-- /myco:agent-awareness -->
