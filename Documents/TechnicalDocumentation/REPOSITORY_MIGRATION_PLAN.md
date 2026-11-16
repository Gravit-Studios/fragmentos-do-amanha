# Repository Migration Plan — Fragmentos do Amanha

Status: active migration plan. Documentation, Artbook, Sprites, Production and helper tooling content have been migrated to the approved structure. Unity relocation remains pending local LFS/GUID validation.

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

The canonical content roots are now Artbook/, Sprites/, Documents/ and Production/. The Unity project remains at unity/FragmentosDoAmanha/ pending its isolated relocation. The Unity project contributes thousands of files. The repository is sizeable, so migration must be incremental and verified.

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

## Remaining Unity relocation

- `unity/FragmentosDoAmanha/` -> `Game/Unity/FragmentosDoAmanha/` only after local Git LFS, object integrity and Unity GUID/reference validation.
- No Unity files or `.meta` files were changed in PR #5.
 
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
Move documents by category; compare duplicate GDD, technical specs, character briefs and visual guidelines; preserve provenance; move prompts and helper scripts; update Markdown and script paths.

### Phase 4 — Migrate Artbook
Initial relocation completed in PR #5. Preserve source pages, indexes and meaningful versions; complete category/index review and validate media locally where possible.

### Phase 5 — Migrate Sprites
Initial relocation completed in PR #5 for existing Theo and Naiara materials. Continue semantic classification of additional characters, weapons, enemies and modular environments as content is added. Preserve PSD, PNG and meaningful versions; do not promote any asset without explicit Aprovado.

### Phase 6 — Move Unity project
1. Confirm Git LFS on the production workstation before large binary moves.
2. Move unity/FragmentosDoAmanha/ as a complete directory to Game/Unity/FragmentosDoAmanha/.
3. Preserve all .meta files and GUIDs.
4. Preserve Assets, Packages, ProjectSettings, manifest and lockfile.
5. Verify ignore rules for Unity caches and local-only files.
6. Open the project from the new path using the recorded Unity version.
7. Validate scenes, prefabs, animation controllers/clips, sprites, tilemaps, scripts and package resolution.
8. Run compile and Play Mode smoke tests on the production workstation.

Exit: no missing references; core scenes and animation references validate; Play Mode test recorded. If Unity is unavailable, mark checks pending rather than claiming success.

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

- [ ] Guide reviewed and merged.
- [ ] README and AGENTS updated.
- [ ] Inventory and integrity report completed.
- [ ] Git LFS verified on production workstation.
- [ ] Destination skeleton created.
- [ ] Documents and tools migrated.
- [ ] Artbook migrated and indexed.
- [ ] Sprites migrated and indexed.
- [ ] Unity moved with GUIDs preserved.
- [ ] Unity Editor validation completed.
- [ ] Approval-to-Unity handoff documented.
- [ ] Final audit and migration report published.

## Out of scope

No game redesign, art repainting/resizing, automatic final-asset selection, historical version deletion, Git history rewrite, Unity package upgrade, Unity version change or scope expansion beyond the current Era Zero + Egypt slice.
