# Current scan: 2 findings; filed: 1

On 2026-11-22, `gh repo view EtharaOrion/kara-samples` resolved the repository as `EtharaLabs/kara-samples`, default branch `main`. The clone fetched commit `6a13364b8196bc76e0299887da7291101102edaf`. A real scan of both current task instructions at that exact commit found 2 STMT_EVAL_FRAMING findings, against 1 originally filed at https://github.com/EtharaLabs/kara-samples/issues/1. The issue's comments query returned no comments. The additional finding is in the second bundle's `dataset/instruction.md`. Both files were successfully retrieved and scanned; neither was unreadable. Historical instruction snapshots under `trajectories/` were excluded from the current task population.

The scan enumerated the committed tree with `git ls-tree -r --name-only HEAD` and supplied the actual `git show HEAD:<path>` bytes to `tools.surface_awareness.instruction_issues(text)`. This avoids treating absent files from the interrupted checkout as clean. There are 20,282 tracked files in the commit; 19,639 trajectory files remain unmaterialized locally. Both live instructions and all other non-trajectory files were recovered. This report therefore gives a measured current framing count, but does not claim complete successor copies.

## Findings and prepared prose

| Path | Line | Class, pattern and matched text | State and evidence | Action | Rewritten sentence |
| --- | ---: | --- | --- | --- | --- |
| `21b44ef3-9bf0-5ac9-92ea-053f42aeef96/instruction.md` | 20 | STMT_EVAL_FRAMING, graded-you, `Your submission is scored` | Conservatively SEALED: samples resident, parent seal/verdict evidence unavailable; root README reports unsealed, but no parent queue or verdict was available to verify that status | Corrected prose in a separate partial copy; complete bundle preparation blocked by missing trajectories | Ensure the trained model generalizes to unseen operand pairs and follow the training and inference requirements above. |
| `c456c486-f4f9-5c5c-b2cd-8a0f127e7462/dataset/instruction.md` | 20 | STMT_EVAL_FRAMING, graded-you, `Your submission is scored` | Conservatively SEALED on the same evidence | Corrected prose in a separate partial copy; complete bundle preparation blocked by missing trajectories | Ensure the trained model generalizes to unseen operand pairs and follow the training and inference requirements above. |

Original disclosure in both files: "Your submission is scored on unseen inputs by an evaluator you cannot see, and how it was produced is reviewed as well as what it scores." The preceding network-installation permission remains. Related screening, grading-scope and parameter-count-measurement sentences were also rewritten as obligations rather than left as residual disclosures. The first task's "Every graded operand carries the full digit width" became "Every operand has exactly eight digits."

Preserved requirements include both exact interfaces, the eight-digit task's `[10,000,000, 99,999,999]` range, the fourteen-digit task's `[0, 99,999,999,999,999]` range, the 99.00% generalization target, minimizing model size, input-dependent self-attention, a model forward pass for every answer, personally trained weights, registered floating-point parameters and accurate metadata, architecture/tokenization/curriculum/optimizer/decoding freedom, separate training code, weights embedded in the delivered module, the exact `/workspace/submission.py` path, standalone import, offline execution, PyTorch availability, installation permission and the prohibition on computing answers outside the model.

## Seal classification evidence

README's Summary and Evidence status sections report 0 sealed bundles, 2 unregistered bundles, no audit verdicts and absent seal digests. Its Dataset structure calls both unsealed. Neither recovered task tree contains a provenance signature outside trajectories, and the committed tree contains no seed queue or audit verdict root. That makes these appear to be legacy unsealed residents, but it does not establish their current parent seal state. Under brief step 3, uncertainty is treated as SEALED, so no in-place edit or push was attempted.

Source review covered the current and retired queue stream readers and verdict readers in `tools/flow/queue.py`, immutable seal/reseal rules in `tools/flow/seal.py`, and byte and mode identity in `tools/bundle_identity.py`. A README's status prose does not replace a verified queue record. No signature, retained verdict or parent seal digest was invented.

## Preparation paths and verification

Root: `/var/folders/pb/ls3p5xx538n5cbwrhxj9xj340000gn/T/opencode/761/kara-samples-successors/`.

| Prepared directory | Available files compared | Missing tracked trajectory files | Changed file | Current-instruction findings after rewrite |
| --- | ---: | ---: | --- | ---: |
| `21b44ef3-9bf0-5ac9-92ea-053f42aeef96/` | 616 | 10,557 | `instruction.md` only | 0 |
| `c456c486-f4f9-5c5c-b2cd-8a0f127e7462/` | 23 | 9,082 | `dataset/instruction.md` only | 0 |

Recursive SHA-256 and permission comparisons passed for all available files in each copy: identical path sets and modes; only the listed instruction changed. Unified diffs showed only the stated prose rewrites. Both prepared current instructions scanned at 0 findings. Missing trajectory files cannot be hashed or diffed, so the brief's full-bundle-copy and all-other-bytes comparison remains incomplete. Historical snapshots already present in the partial copy were preserved, not rewritten. No task code changed; build/runtime tests and full CRUCIBLE review did not run.

## Checkout failure and recovery

The required clone was invoked with bash workdir exactly `/var/folders/pb/ls3p5xx538n5cbwrhxj9xj340000gn/T/opencode/761`:

```sh
GIT_MASTER=1 git clone --filter=blob:none https://github.com/EtharaLabs/kara-samples.git kara-samples
```

After 600,000 ms the tool terminated the command. Git reported:

```text
Cloning into 'kara-samples'...
warning: Clone succeeded, but checkout failed.
You can inspect what was checked out with 'git status'
and retry with 'git restore --source=HEAD :/'
```

This was a checkout timeout, not the earlier maintainer-guard refusal. The clone had a committed tree but initially no working files. `git count-objects -vH` reported 2,003 objects in a 673.78 KiB pack and an interrupted 155.94 MiB temporary pack. Tree inspection established that nearly all tracked paths are trajectory artifacts, rather than a small task-only repository.

From inside this clone, recovery of the README and two current instructions succeeded. Recovery of the entire first bundle with `git restore --source=HEAD --worktree -- 21b44ef3-9bf0-5ac9-92ea-053f42aeef96` then exceeded 540,000 ms and was terminated. A third, narrower recovery succeeded:

```sh
GIT_MASTER=1 git restore --source=HEAD --worktree -- . ':(exclude)**/trajectories/**'
```

At comparison time, all missing paths were under trajectories: 10,557 in the first bundle and 9,082 in the second. No non-trajectory path was missing. All commands ran within the clone after cloning and had timeouts of at most 10 minutes. No guard refusal was bypassed, and no original remote bytes changed.

## Operator command list, not executed

First finish materializing both complete bundles at the recorded commit and merge the two prepared instruction corrections into complete comparison copies without changing other bytes. Do not treat these partial directories as minted or sealable successors. Recheck the parent queue/verdict state. If the legacy bundles are proved unsealed, use a documented owning-run draft path rather than editing the samples root by hand. If they are sealed, obtain a current retained verdict before successor authoring.

At the owning kara parent root, the documented audit and author entry commands for the two task scopes are:

```sh
uv run --project ./trinity --no-dev ./trinity/tools/brief.py ./ --door audit --task 21b44ef3-9bf0-5ac9-92ea-053f42aeef96 --mode me
uv run --project ./trinity --no-dev ./trinity/tools/brief.py ./ --door author --task 21b44ef3-9bf0-5ac9-92ea-053f42aeef96 --mode me
uv run --project ./trinity --no-dev ./trinity/tools/brief.py ./ --door audit --task c456c486-f4f9-5c5c-b2cd-8a0f127e7462 --mode me
uv run --project ./trinity --no-dev ./trinity/tools/brief.py ./ --door author --task c456c486-f4f9-5c5c-b2cd-8a0f127e7462 --mode me
```

If scope validation refuses a legacy unregistered resident, stop at that refusal and have the owning operator establish its lawful authoring path; these commands confer no adoption authority. Complete each emitted brief and its approval, retirement, build, mint, binding, route and review steps. At the actual seal step, enter the real run id and newly minted UUID from the brief into these standard-input reads. Seal once only if the author flow has not already sealed the successor:

```sh
read -r FORGE_RUN
read -r SUCCESSOR_UUID
uv run --project ./trinity --no-dev ./trinity/tools/pipeline.py seal ./ "$SUCCESSOR_UUID" --run-id "$FORGE_RUN"
uv run --project ./trinity --no-dev ./trinity/tools/brief.py ./ --door audit --task "$SUCCESSOR_UUID" --mode me
```

Sources: `templates/doors/commands/{author,audit}.md`, `forge/author-loop.md`, `forge/phase-build.md:20-24`, `forge/phase-verify.md:113-127`, `forge/phase-release.md:30-40`, ADR 0314 and `tools/refusal_guide.py:3893-3899`. No `--supersede` route applies.

## Detector and unresolved work

Detector: read-only `/Users/sarvex/Knowledge/worktrees/749-provenance`, `tools.surface_awareness.instruction_issues(text)` and `surface_eval_classes.py`, imported using `PYTHONDONTWRITEBYTECODE=1` and `python3 -B`. SHA-256: `surface_awareness.py` = `99b68f90df3c58733c287b7eff9932bc1c8bcb38f5b4c7136e6a1ee2a9c8b3a7`; `surface_eval_classes.py` = `a5cdc4fdc8cdf6f34cff372bcf9a592727101902585481aec79c11053f052c07`. Trinity #761's third update was read before this repository was processed.

Maintainer decision: Prepare successors, no seal. Pushes and commit ids: none. Nothing was sealed or signed; no FORGE/CRUCIBLE run or issue write occurred. The real scan and both requirement-preserving instruction corrections are complete. Full copies and comparison of the 19,639 missing trajectory files are not complete because the clone and targeted full-bundle recovery timed out. Parent seal status and lawful legacy-resident scope also remain unverified. These gaps are explicit; no full-successor or remediation-completion claim is made.
