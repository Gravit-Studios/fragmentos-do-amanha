# Unity Project Relocation Report — 2026-11-16

## Result

The complete Unity project is now proposed at `Game/Unity/FragmentosDoAmanha/`. The former `unity/` root was removed from the proposed tree. The Unity project was moved by reusing its original Git subtree object rather than rebuilding individual files.

## Integrity evidence from GitHub tree

- Original Unity project subtree SHA: `f792c361bcfed6234a511cac3be64524ebae5a85`.
- Destination subtree SHA: `f792c361bcfed6234a511cac3be64524ebae5a85` (identical).
- Tracked project blobs: 6,627.
- Unity `.meta` files: 3,463.
- LFS pointer candidates inside the Unity project: 308.
- Required files present: `Packages/manifest.json`, `Packages/packages-lock.json`, and `ProjectSettings/ProjectVersion.txt`.
- No tracked Unity cache/build directories such as Library, Temp, Logs, UserSettings, Obj or Builds were found in the project tree.
- No submodules were found in the Unity subtree.

Because the subtree SHA is identical, every file blob and every `.meta` file is unchanged. This preserves the existing GUIDs and serialized Unity references at the Git object level.

## Not verified remotely

GitHub tree inspection does not verify that the external Git LFS objects can be downloaded, nor does it run Unity Editor. The production workstation must complete the checks below before the migration can be considered fully validated.

## Required workstation checklist

Run from the repository root after closing Unity Editor:

```bash
git pull --ff-only origin main
git lfs version
git lfs pull
git lfs fsck
```

Then open `Game/Unity/FragmentosDoAmanha/` in Unity `6000.5.3f1` and:

1. Wait for package resolution and asset import to finish.
2. Inspect the Console for compilation, import and missing-reference errors.
3. Open `Assets/Scenes/Prototype_Theo_Controller.unity`.
4. Open `Assets/Scenes/VS_EraZero_Lab.unity` and `Assets/Scenes/VS_Egypt_Blockout.unity`.
5. Run a Play Mode smoke test covering movement, jump, dash, combat, health/respawn, fragment collection and the temporal portal.
6. Record any errors and the test result in `Production/Status/Current-Status.md`.

Do not delete any old local working copy until the new project path has opened and passed validation.
