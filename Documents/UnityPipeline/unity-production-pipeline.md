# Unity Production Pipeline

## Canonical project location

The complete Unity project is maintained at:

`Game/Unity/FragmentosDoAmanha/`

Open that folder in Unity Hub. Do not open the repository root as a Unity project.

## Project baseline

- Unity Editor: `6000.5.3f1` (see `ProjectSettings/ProjectVersion.txt`).
- Render pipeline: Universal Render Pipeline 2D.
- Input: Input System.
- Packages and exact resolved versions: `Packages/manifest.json` and `Packages/packages-lock.json`.

## Asset lifecycle

- Working artwork and editable masters live in `Sprites/`.
- Only assets explicitly approved by the user with **Aprovado** may be copied to `Game/ApprovedAssets/`.
- Integrate the approved export into `Game/Unity/FragmentosDoAmanha/Assets/` only after approval.
- Preserve Unity `.meta` files and GUIDs. Never recreate them manually.

## Safe local update after repository relocation

1. Close Unity Editor.
2. Run `git pull --ff-only origin main` from the repository root.
3. Confirm Git LFS is installed and all objects are available.
4. Open `Game/Unity/FragmentosDoAmanha/` in Unity Hub.
5. Wait for asset import and package resolution.
6. Check Console, open the primary scenes and run Play Mode smoke tests.

The repository move preserves Git tree/blob identities; it does not replace local Editor validation.
