# Migration Status — updated 2026-11-16

## Completed

- [x] Final organization decisions captured in the official guide.
- [x] PR #1 merged: organization guide and phased migration plan.
- [x] PR #2 merged: AGENTS.md and README.md aligned with the approved transition policy.
- [x] Phase 0 repository tree inventory captured.
- [x] Git LFS pointer format verified against representative PNG and PDF objects.
- [x] PR #3 merged: target directory skeleton and category READMEs created.
- [x] Phase 2 destination structure is present on main.
- [x] PR #5 merged: 209 files relocated from legacy roots into Artbook/, Documents/, Production/ and Sprites/.
- [x] Removed duplicate lowercase roots artbook/, docs/, production/, sprites/ and legacy roots ChatGPT/ and tools/.
- [x] PR #7 moved the complete Unity project subtree to Game/Unity/FragmentosDoAmanha/; original tree SHA preserved.

## In progress / pending

- [ ] Confirm Git LFS installation, fetch and fsck on the production workstation.
- [ ] Validate LFS object availability and sample image/PDF opening locally.
- [ ] Review the seven large executables inside the embedded Unity AI Assistant package; the package is declared in Packages/manifest.json and must not be pruned without a separate dependency decision.
- [x] GitHub tree comparison confirms all 3,463 Unity .meta files remain in the moved project subtree.
- [ ] Open moved project in Unity Editor and validate references/package resolution.
- [ ] Complete semantic review of migrated categories and update remaining cross-document references.


## Repository snapshot

- Main baseline after policy PRs and target skeleton: `dc7f0bce72f36d4f881896e3c55206825cf13276`.
- Recursive tree inventory before skeleton creation: 7,454 entries (6,844 blobs and 610 tree entries).
- Git tree blob-size sum: approximately 526 MB.
- GitHub repository metadata size: 309,235 KB.
- Unity metadata files in the original inventory: 3,463.
- 417 files with LFS-managed extensions have pointer-sized Git blobs. Representative PNG and PDF contents were confirmed as valid Git LFS pointer text.
- Seven executable files of approximately 24–101 MB each are present under the embedded `com.unity.ai.assistant` package. Preserve pending dependency review.

## Active paths during transition

The Unity project is now at `Game/Unity/FragmentosDoAmanha/`.
All non-Unity content roots now use the approved canonical names.

New artwork is produced in `Sprites/`; only assets explicitly approved with **Aprovado** may be promoted to `Game/ApprovedAssets/`.

## Next execution batch

Complete local Git LFS verification and Unity Editor/Play Mode validation.
