# Minimal 14-digit addition transformer

Create `/workspace/submission.py` implementing the interface below:

- `build_model() -> (model, metadata)` returns a `torch.nn.Module` and metadata dictionary.
- `add(model, a: int, b: int) -> int` returns the exact sum for operands in `[0, 99,999,999,999,999]`.

The goal is to build the smallest trained transformer that reaches at least 99.00% held-out accuracy on unseen operand pairs. A working submission is a starting point rather than a finish line: keep making it smaller while it still meets the accuracy bar.

The model must be a genuine transformer that learns the task. Its self-attention must do real work, meaning the attention it computes depends on its input rather than being a fixed pattern dressed up as attention. Every answer `add` returns must be produced by a forward pass of the returned model, and the weights that produce it must come from training you ran yourself. All learned floating-point values must be registered parameters; report the actual parameter count accurately in the metadata.

You may change the architecture, tokenization, data generator, curriculum, optimizer, and decoding loop. A working but deliberately weak baseline ships in the workspace as `submission.py`, with its trainer alongside as `train.py`.

Training code must live outside `submission.py`. Keep only the model, trained weights and inference path in `submission.py`, with a small dependency surface; do not generate labelled training data there. Train in a separate file and write the resulting weights into `submission.py`, which is what the shipped `train.py` does. The delivered module must work when imported on its own.

`/workspace` is writable: place the finished file at exactly `/workspace/submission.py`, never leave it only under `work/` or a host path. The development environment has PyTorch and network access for its model service; the delivered module must support offline execution.

Solving this task means the model learns to add. Everything the answer depends on must be learned by your training and computed by the model; nothing about the result may be worked out elsewhere and handed to it. Where you place code does not change what it is.

You may use the network to install packages and download tooling. Ensure the trained model generalizes to unseen operand pairs and follow the training and inference requirements above.
