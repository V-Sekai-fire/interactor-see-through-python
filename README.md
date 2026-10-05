# interactor-see-through-python

The Python reference half of the see-through A/B: single-image layer decomposition for illustrated characters, on the harness command bus.

## What it is for

It runs the upstream see-through pipeline over PyTorch behind the same command bus as the C++ half, `interactor-see-through-ggml`, and the two share nothing but the wire, so a disagreement between them is a finding. Runs below a resolution and step-count floor are refused, because low settings make layers that look plausible and say nothing about quality. `proof/test_agreement.py` fails when the two halves stop refusing the same runs. The container image runs the interactor beside a transport layer and reads the weights from a mounted volume rather than carrying them.

## Build and run

```sh
python -m seethrough
python3 proof/test_command.py
```

The first serves the interactor on the bus; the second checks the command parsing and the floor without a bus, a GPU or weights.

## Licence

`LICENSE` is MIT, while the package metadata and the source headers declare Apache-2.0; the two disagree.
