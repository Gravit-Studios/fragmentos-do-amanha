# Repository Migration Plan — Fragmentos do Amanha

Status: prepared plan. No production assets or Unity project have been moved by this change.

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

The repository currently contains artbook/, sprites/, docs/, ChatGPT/, production/, tools/ and unity/FragmentosDoAmanha/, plus root project instructions and configuration. The Unity project contributes thousands of files. The repository is sizeable, so migration must be incremental and verified.

## Initial source-to-target map

- unity/FragmentosDoAmanha/ -> Game/Unity/FragmentosDoAmanha/ (move complete project as one unit; preserve .meta files and GUIDs).
- artbook/branding/ -> Artbook/Branding/.
- artbook/illustration/characters/ -> Artbook/CharacterDesign/.
- artbook/illustration/environments/ -> Artbook/EnvironmentDesign/.
- artbook/pixel-reference/ -> Artbook/VisualReferences/PixelArt/.
- artbook/concept-book/ and artbook/pdf/ -> Artbook/Publications/.
- sprites/Theo/ and sprites/Naiara/ -> Sprites/Characters/<Character>/, sorted into concepts, studies, sheets and animation actions.
- docs/03_VisualDevelopment/prompts/ -> Production/Prompts/ by asset category.
- durable docs/03_VisualDevelopment standards -> Documents/ArtDirection/.
- docs/04_Characters/ and ChatGPT/personagens/ -> Documents/Characters/, after comparison.
- docs/06_Animation/ -> Documents/Animation/.
- docs/08_UnityPipeline/ -> Documents/UnityPipeline/.
- ChatGPT/GDD.md and ChatGPT/ESPECIFICACOES-TECNICAS.md -> Documents/GDD/ and Documents/TechnicalDocumentation/, after comparing against current docs.
- ChatGPT/game-design/ -> Documents/GameDesign/.
- ChatGPT/narrativa/ -> Documents/Narrative/.
- ChatGPT/nomes/ -> classify into Documents/WorldBible/ or Documents/GameDesign/ after content review.
- production status, handoff and roadmap -> Production/Status/ and Production/Roadmap/.
- tools/art-pipeline/ -> Production/Tools/ArtPipeline/.

This is a routing map, not a blind move list. Inspect content, references and binary validity before moving each batch.

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
Move branding, concept book, illustrations, pixel references and publications. Preserve source pages, indexes and meaningful versions. Validate PDFs and images.

### Phase 5 — Migrate Sprites
Separate protagonists, enemies and bosses. Organize weapons by era then character. Organize environments by era/location and modular function. Preserve PSD, PNG and meaningful versions. Do not promote any asset without explicit Aprovado.

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
