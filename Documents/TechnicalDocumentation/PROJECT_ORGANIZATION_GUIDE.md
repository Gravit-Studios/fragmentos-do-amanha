# Project Organization Guide — Fragmentos do Amanha

Status: approved standard, implemented in the repository.

## Purpose
This guide defines repository responsibilities, asset lifecycle, naming, approval and Unity safety rules. English is used for paths and filenames; explanatory documentation remains in Portuguese where appropriate.

## Target structure

- Game/ApprovedAssets/: release/handoff package containing only assets explicitly approved by the user.
- Game/Unity/FragmentosDoAmanha/: complete Unity project, including Assets, Packages and ProjectSettings.
- Artbook/: presentation art, concepts, character/environment design, worldbuilding, references, branding and publications.
- Sprites/: working source for game-ready art, including PSD masters, PNG exports, drafts, studies, sprite sheets and meaningful version history.
- Documents/: authoritative GDD, world bible, narrative, character, game design, art direction, animation, technical and Unity pipeline documentation.
- Production/: prompts, workflows, scripts, tools, status and roadmap.

Suggested full tree:

    Game/
      ApprovedAssets/{Characters,Environments,Weapons,Assets,Tilesets,VFX,UI}/
      Unity/FragmentosDoAmanha/{Assets,Packages,ProjectSettings}/
    Artbook/{Branding,CharacterDesign,EnvironmentDesign,ConceptArt,Worldbuilding,VisualReferences,Publications}/
    Sprites/{Characters,Scenarios,Assets,Weapons,AnimationSheets,VFX,UI,Templates}/
    Documents/{GDD,WorldBible,Narrative,Characters,GameDesign,ArtDirection,Animation,TechnicalDocumentation,UnityPipeline,Production}/
    Production/{Prompts,Workflows,Scripts,Tools,Status,Roadmap}/

## Category rules

Characters are separated into protagonists, enemies and bosses. Each character has concept, studies, sprite sheets, animation actions and approved export areas as needed. Enemies and bosses must not be mixed into the protagonist folders.

Weapons are organized by historical era, then by wielder/character and weapon: Sprites/Weapons/<Era>/<Character>/<WeaponName>/. Shared equipment can use a Shared subfolder within an era.

Environments are modular-first and organized by era and location. Suggested categories are Tilesets, Gameplay, Background, Parallax, Foreground, Props and SetPieces. Full-scene images may be kept as concepts or special presentation art, but do not replace modular pieces where collision, reuse, sorting or parallax require independent assets.

Artbook is organized by category, not creation date. Keep concepts, references and presentation material out of runtime assets.

## Asset lifecycle

1. Create and iterate in the matching Sprites working folder.
2. Preserve editable PSD source and PNG exports, plus all meaningful versions and studies.
3. Run technical and visual QA.
4. Wait for the user's explicit message: Aprovado. Technical compliance alone never grants approval.
5. Copy the selected approved export into Game/ApprovedAssets.
6. Integrate that exact export into Game/Unity/FragmentosDoAmanha/Assets and configure Unity import settings, pivots, slicing, sorting and animation as required.
7. Record source version, approval, destination and any conversion in an asset index or handoff note.

A later visual change is a new version and must be approved again. Do not edit the Unity copy as the artwork master.

## Formats and naming

PSD is the editable master where applicable. PNG is the lossless export and standard runtime image format. Aseprite source may be retained when used, but is not mandatory. Preserve all meaningful versions. Use lowercase English snake_case names and explicit version suffixes, for example theo_idle_01_v01.png, theo_run_sheet_v02.png, egypt_temple_ground_v01.png and theo_temporal_scanner_v01.png. Avoid spaces, accents and ambiguous names such as final_final2.

## Current visual baselines

Use the current Pixel Art Bible and approved project documents as source of truth. Baselines include approximately 64x96 px for a character canvas, 32x32 px base tiles and suggested PPU 32. Maintain crisp pixel edges, readable silhouettes, consistent palette and animation alignment. These are baselines, not permission to resize existing art without checking its actual dimensions and Unity importer settings.

## Unity safety

- Preserve every Unity .meta file and GUID when moving or renaming assets.
- Move the entire Unity project as one unit; keep Assets, Packages and ProjectSettings together.
- Do not commit Library, Temp, Logs, UserSettings, crash logs or local caches.
- Do not fabricate or manually edit scenes/prefabs when Unity Editor is required.
- Reopen `Game/Unity/FragmentosDoAmanha/` and validate scenes, prefabs, scripts, sprites, animation clips/controllers and package resolution in Unity Editor.
- Confirm Git LFS is installed and configured on the production workstation; the project relocation is structurally complete, but LFS object integrity must be checked locally.

## Document precedence

Explicitly approved user decisions take precedence, followed by AGENTS.md and current operational status/handoff, then current approved design/technical bibles, then older imported references. Do not delete conflicting legacy documents during migration; preserve provenance and reconcile separately.

## Change control

Use a dedicated migration branch. Keep policy/documentation changes separate from bulk binary moves. No force pushes, history rewrites or bulk deletions. Each migration batch needs a source-to-destination manifest, validation and review.
