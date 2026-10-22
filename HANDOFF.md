# HANDOFF — Spirit-model-assets

Flux LoRA models for RunPod serverless deployment (per `README.md`). Repo has
one commit, `ba696ba init`, on branch `main`. Remote: `isndotbiz/spirit-model-assets`.
`git ls-files` lists exactly one tracked file: `README.md`. No LoRA weights or
other assets are committed.

## Public/private
`gh repo view --json visibility,nameWithOwner,isPrivate` reports:
`isPrivate: false`, `visibility: PUBLIC`, `nameWithOwner: isndotbiz/spirit-model-assets`.
This repo is **public** on GitHub right now.

## .gitignore
Current `.gitignore` has one real rule plus comments:
```
png-masters/
```
With the explanatory comment that `png-masters/` holds 294M of PNG masters
rescued 2026-08-21 from a stale website clone — the only surviving masters
(the CDN has only `.webp` derivatives) — deliberately kept untracked because
294M of binaries don't belong in git history, with B2 or git-lfs proposed as
the proper home, backstopped meanwhile by the restic workspace backup.

**Proposal:** given the repo is public, keep `png-masters/` ignored exactly as
it is (do not add or LFS-track these binaries into a public repo) and add
standard local-noise entries (`__pycache__/`, `*.pyc`, `node_modules/`,
`.DS_Store`) if any such tooling is later added to this repo. No change to
`.gitignore` was made in this pass — this is a proposal only.

## png-masters backup plan
**`png-masters/` does not currently exist on disk anywhere searched on this
host** (checked `~/Workspace` and a wider filesystem search) — the directory
the `.gitignore` comment describes is absent from this working copy. Possible
explanations: it lives only on another host, was never restored after a
migration, or was removed. This should be verified before relying on it.

Proposed backup plan once/if the files are located:
1. Confirm current location and the restic workspace backup actually covers it
   (the `.gitignore` comment claims this; not independently verified here).
2. Move the 294M of masters to Backblaze B2 (the `wslcrypt` B2 crypt remote is
   already in use for other workspace backups) or git-lfs, per the ignore
   comment's own stated intent — do not add them to git history directly.
3. Keep `png-masters/` in `.gitignore` regardless of destination, since this
   repo is public.

No files were moved, deleted, or uploaded in this pass — proposal only, per
instruction.
