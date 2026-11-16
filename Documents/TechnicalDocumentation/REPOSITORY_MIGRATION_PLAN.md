# Repository Migration Plan — Fragmentos do Amanha

Status: content and Unity project relocation merged. Remaining completion gate: local Git LFS verification and Unity Editor/Play Mode validation.

## Approved decisions

- Keep working Sprites separate from approved Game deliverables.
- Promote assets only after the user explicitly says Aprovado.
- PSD editable masters and PNG exports.
- Preserve all meaningful versions and studies.
- Organize Artbook by category.
- Move the complete Unity project to Game/Unity/FragmentosDoAmanha.
- English paths and filenames.
- Weapons organized by era, then character/wielder.
- Separate Enemies and Bosses collections.
- Modular-first environments: tilesets, gameplay pieces, props and parallax layers.
- Maintain an official organization guide.

## Current roots inspected

The canonical content roots are Artbook/, Sprites/, Documents/, Production/ and Game/Unity/FragmentosDoAmanha/. The complete Unity project subtree has been relocated without changing its Git tree SHA.

## Completed content relocation (PR #5)

- `artbook/branding/` -> `Artbook/Branding/Logo/`.
- `artbook/concept-book/` -> `Artbook/Publications/ConceptBook/`.
- `artbook/illustration/characters/` -> `Artbook/CharacterDesign/Illustrations/Characters/`.
- `artbook/illustration/environments/` -> `Artbook/EnvironmentDesign/Illustrations/Environments/`.
- `artbook/pixel-reference/` -> `Artbook/VisualReferences/PixelArt/`.
- `artbook/pdf/` -> `Artbook/Publications/PDF/`.
- `docs/` and `ChatGPT/` -> categorized subfolders under `Documents/`.
- `production/` and `tools/art-pipeline/` -> `Production/Status/`, `Production/Roadmap/`, `Production/Workflows/` and `Production/Tools/ArtPipeline/`.
- `sprites/Theo/` -> `Sprites/Characters/Theo/`, separated into Source, References and Animation actions.
- `sprites/Naiara/` -> `Sprites/Characters/Naiara/References/`.
- The six legacy roots were removed after relocation. Original blob SHAs were reused to preserve file contents and LFS pointer data.

## Unity relocation completed in PR #7

- The complete `unity/FragmentosDoAmanha/` subtree was moved to `Game/Unity/FragmentosDoAmanha/` by reusing its original Git tree SHA.
- All 6,628 file blobs and 3,463 `.meta` files were preserved unchanged, retaining GUIDs.
- No scene, prefab, asset, package or ProjectSettings contents were rewritten.
- Local Git LFS object verification and Unity Editor validation remain mandatory.
 
## Migration phases

### Phase 0 — Inventory and safety baseline
1. Confirm current main SHA and inspect active branches/PRs.
2. Export a complete path inventory, file counts and size report.
3. Identify large binaries and verify Git LFS installation/tracking policy.
4. Validate image signatures and dimensions. Some current image paths have unusually small reported blob sizes and must be inspected before being treated as valid image assets.
5. Detect duplicate content by hash, not filename alone.
6. Record Unity .meta files/GUIDs and references from scenes, prefabs, animation clips/controllers and scripts.

Exit: inventory, integrity report, LFS decision and Unity GUID baseline documented.

### Phase 1 — Publish rules
1. Add the organization guide.
2. Update root README and AGENTS.md with new paths and approval gate.
3. Update links in current status, roadmap and handoff.
4. Keep policy changes separate from bulk file moves.

Exit: documentation links resolve and no old path instruction contradicts the new policy.

### Phase 2 — Create destination skeleton
Create target directories and concise README/index files. Do not move assets yet.

### Phase 3 — Migrate documentation and tools
Initial relocation completed in PR #5. Complete remaining cross-document link/reference normalization and semantic index review.

### Phase 4 — Migrate Artbook
Initial relocation completed in PR #5. Preserve source pages, indexes and meaningful versions; complete category/index review and validate media locally where possible.

### Phase 5 — Migrate Sprites
Initial relocation completed in PR #5 for existing Theo and Naiara materials. Continue semantic classification of additional characters, weapons, enemies and modular environments as content is added. Preserve PSD, PNG and meaningful versions; do not promote any asset without explicit Aprovado.

### Phase 6 — Move Unity project
Completed structurally in PR #7. The GitHub tree move preserved the complete project and all GUID-bearing metadata. Remaining local exit checks: confirm Git LFS with `git lfs version`, `git lfs pull` and `git lfs fsck`; open the new path in Unity `6000.5.3f1`; inspect Console; open core scenes; run compile and Play Mode smoke tests. These checks cannot be performed by a GitHub tree operation.

### Phase 7 — Approved asset handoff
Define export/import presets. For each user-approved asset, copy the selected export to Game/ApprovedAssets and integrate the exact export into the Unity Assets folder. Configure PPU, sprite mode, slicing, pivot, filter/compression, sorting and animation settings as appropriate. Record source version and destination. Validate in-game.

### Phase 8 — Final audit
Search old path references; check duplicate hashes and untracked files; ensure no caches were committed; validate README/index links; update status, roadmap and handoff; publish a migration report.

## Risks and mitigations

- Unity reference breakage: move the complete project and preserve .meta/GUIDs; validate in Editor.
- Binary growth/LFS mismatch: audit first and configure LFS before bulk moves.
- Corrupt/placeholder images: inspect signatures and dimensions before categorizing.
- Conflicting design docs: compare content and provenance; retain originals until resolved.
- Broken links/scripts: keep a move manifest and run path checks.
- Draft accidentally promoted: require explicit Aprovado.
- Competing masters: PSD/source stays in Sprites; approved export is release package; Unity is integration copy.

## Git strategy

Use a dedicated migration branch; never perform the full migration directly on main. Separate documentation from binary move batches. Use Git-aware moves where possible. Avoid force pushes, history rewrites and bulk deletes. Review each batch diff. Keep Unity relocation isolated so it can be reverted independently.

## Completion checklist

- [x] Guide reviewed and merged.
- [x] README and AGENTS updated.
- [x] Inventory and GitHub tree integrity report completed; local LFS verification remains pending.
- [ ] Git LFS verified on production workstation (local check).
- [x] Destination skeleton created.
- [x] Documents and tools migrated.
- [x] Artbook migrated and category README updated.
- [x] Initial Sprites relocation completed; semantic review of additional categories remains ongoing.
- [x] Unity moved with original subtree SHA and GUID-bearing `.meta` files preserved.
- [ ] Unity Editor validation completed.
- [x] Approval-to-Unity handoff documented.
- [ ] Final audit after local LFS and Unity Editor validation.

## Out of scope

No game redesign, art repainting/resizing, automatic final-asset selection, historical version deletion, Git history rewrite, Unity package upgrade, Unity version change or scope expansion beyond the current Era Zero + Egypt slice.
