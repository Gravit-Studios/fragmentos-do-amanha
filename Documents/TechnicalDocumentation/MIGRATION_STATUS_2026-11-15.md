# Migration Status — 2026-11-15

## Completed

- [x] Final organization decisions captured in the official guide.
- [x] PR #1 merged: organization guide and phased migration plan.
- [x] PR #2 merged: AGENTS.md and README.md aligned with the approved transition policy.
- [x] Phase 0 repository tree inventory captured.
- [x] Git LFS pointer format verified against representative PNG and PDF objects.
- [x] PR #3 merged: target directory skeleton and category READMEs created.
- [x] Phase 2 destination structure is present on main.

## In progress / pending

- [ ] Confirm Git LFS installation, fetch and fsck on the production workstation.
- [ ] Validate LFS object availability and sample image/PDF opening locally.
- [ ] Review the seven large executables inside the embedded Unity AI Assistant package; the package is declared in Packages/manifest.json and must not be pruned without a separate dependency decision.
- [ ] Capture Unity .meta GUID inventory and baseline Editor validation on the production workstation.
- [ ] Migrate legacy documentation and production tooling in reviewed batches.
- [ ] Migrate Artbook content and update references.
- [ ] Migrate working Sprites and update asset indexes.
- [ ] Relocate Unity project only after local LFS and GUID checks pass.

## Repository snapshot

- Main baseline after policy PRs and target skeleton: `dc7f0bce72f36d4f881896e3c55206825cf13276`.
- Recursive tree inventory before skeleton creation: 7,454 entries (6,844 blobs and 610 tree entries).
- Git tree blob-size sum: approximately 526 MB.
- GitHub repository metadata size: 309,235 KB.
- Unity metadata files in the original inventory: 3,463.
- 417 files with LFS-managed extensions have pointer-sized Git blobs. Representative PNG and PDF contents were confirmed as valid Git LFS pointer text.
- Seven executable files of approximately 24–101 MB each are present under the embedded `com.unity.ai.assistant` package. Preserve pending dependency review.

## Active paths during transition

The Unity project remains at `unity/FragmentosDoAmanha/`. Do not move it manually.
The target destination is `Game/Unity/FragmentosDoAmanha/`.

New artwork is produced in `Sprites/`; only assets explicitly approved with **Aprovado** may be promoted to `Game/ApprovedAssets/`.

## Next execution batch

Start with documentation and Artbook content because those moves do not require Unity Editor serialization. Preserve source provenance, keep an old-to-new path manifest, and update all Markdown links in the same migration batch. The Unity relocation remains isolated and blocked on local Git LFS and Editor validation.
