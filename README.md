# Peras networks

Evaluation networks for the [Peras](https://github.com/FirePlank/Peras) chess engine.

They live here rather than in the engine repository because each one is tens of megabytes, and every release would otherwise add that to the history permanently. Every network the engine has shipped is kept, so any tagged commit can still be built.

Each network is attached to a release, both raw and zstd-compressed. Download the one matching the engine version you are building.

| Network | Engine versions | Architecture | Size |
| ------- | --------------- | ------------ | ---- |
| `peras-v3.nnue` | v3.0.0 and later | `(768x10hm + threats + pawn pairs -> 1024)x2 -> 8` | 78 MB |
| `peras-v2.nnue` | v2.0.0 to v2.1.0  | `(768x10hm -> 1024)x2 -> 8` | 15 MB |

The architectures are not interchangeable. The engine embeds the network at compile time and the file size is part of the type, so building against the wrong one fails to compile rather than playing badly.

## Building the engine with one of these

Save the network as `nets/peras.nnue` in the engine source root, or point `EVALFILE` at it:

```bash
curl -sL https://github.com/FirePlank/Peras-networks/releases/download/peras-v3/peras-v3.nnue -o nets/peras.nnue
cargo build --release
```

## Licence

The networks are trained on data provided by the [Leela Chess Zero](https://lczero.org/) project, made available under the [Open Database License](https://opendatacommons.org/licenses/odbl/1-0/), with individual contents under the [Database Contents License](https://opendatacommons.org/licenses/dbcl/1-0/).
