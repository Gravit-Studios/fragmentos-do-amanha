# Migration Status — 2026-11-15

## Completed

- [x] Final organization decisions captured in the official guide.
- [x] Pull Request #1 merged: organization guide and phased migration plan.
- [x] Pull Request #2 merged: AGENTS.md and README.md aligned with the approved transition policy.
- [x] Phase 0 repository tree inventory captured in REPOSITORY_INVENTORY_2026-11-15.md.
- [x] Git LFS pointer format verified against representative PNG and PDF objects.
- [x] Phase 2 target directory skeleton created on the migration branch.

## In progress / pending

- [ ] Confirm Git LFS installation, fetch and fsck on the production workstation.
- [ ] Validate all LFS object availability and sample image/PDF opening locally.
- [ ] Review the seven large executables inside the embedded Unity AI Assistant package; package is referenced by Packages/manifest.json and must not be pruned without a separate dependency decision.
- [ ] Capture Unity .meta GUID inventory and baseline Editor validation on the production workstation.
- [ ] Review target skeleton and merge Phase 2.
- [ ] Migrate documentation, Artbook and Sprites in separate reviewed batches.
- [ ] Relocate Unity project only after local LFS and GUID checks pass.

## Repository snapshot

- Main baseline after policy PRs: `701dfc264c59e9dc3b3ef78d59d545b5379d1d34`.
- Recursive tree inventory: 7,454 entries (6,844 blobs and 610 tree entries in the captured snapshot before the latest skeleton commits).
- Git tree blob-size sum: approximately 526 MB.
- GitHub repository metadata size: 309,235 KB.
- Unity metadata files in the original inventory: 3,463.
- LFS-managed extension files with pointer-sized Git blobs: 417 candidates. Sample PNG and PDF contents confirmed valid Git LFS pointer structure.
- Seven executable files of approximately 24–101 MB each are present under the embedded `com.unity.ai.assistant` package. They are part of a declared embedded dependency; preserve pending review.

## Active paths during transition

The Unity project remains at `unity/FragmentosDoAmanha/`. Do not move it manually.
The target destination is `Game/Unity/FragmentosDoAmanha/`.

New artwork is produced in `Sprites/`; only assets explicitly approved with **Aprovado** may be promoted to `Game/ApprovedAssets/`.
