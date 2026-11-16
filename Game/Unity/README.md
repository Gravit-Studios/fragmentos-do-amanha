# Unity Project

Canonical Unity project path:

`Game/Unity/FragmentosDoAmanha/`

Open the `FragmentosDoAmanha` folder in Unity Hub, not the repository root.

The complete project was relocated as a Git tree, preserving the original subtree and all tracked file blobs, including 3,463 Unity `.meta` files and their GUIDs. The move did not rewrite scenes, prefabs, assets, packages or ProjectSettings.

## Local validation required

On the production workstation:

1. Close Unity Editor and Unity Hub project sessions before updating the repository.
2. Run `git pull --ff-only origin main`.
3. Confirm Git LFS is installed with `git lfs version`.
4. Fetch and verify LFS objects with `git lfs pull` and `git lfs fsck`.
5. Open `Game/Unity/FragmentosDoAmanha/` using Unity `6000.5.3f1`.
6. Wait for import/package resolution; check Console for errors.
7. Open the prototype and vertical-slice scenes, then run a Play Mode smoke test.

Do not delete the previous local folder manually until the new path has opened and passed validation. The GitHub repository no longer contains the old `unity/FragmentosDoAmanha/` path.
