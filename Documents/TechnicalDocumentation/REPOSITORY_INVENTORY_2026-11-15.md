# Repository Inventory — 2026-11-15

## Snapshot
- Repository: `Gravit-Studios/fragmentos-do-amanha`
- Branch: `main`
- Baseline after organization-plan merge: `8cc8eb9f4a38be3fd2885eb1c7acc0db7a07508e`
- Tree entries: 7454
- Blobs/files: 6844
- Directories: 610
- Sum of Git tree blob sizes: 526451517 bytes
- GitHub repository API size: 309235 KB (repository metadata; not directly comparable with tree blob-size sum).

## Top-level legacy roots
`ChatGPT/`, `Documents/`, `artbook/`, `Documents/`, `production/`, `sprites/`, `tools/`, `unity/`.

## Git LFS and binary observations
- `.gitattributes` already declares LFS filters for image/source art, PDFs, audio, video, 3D sources and selected binary bundles.
- 417 files with LFS-managed extensions have Git tree entries below 200 bytes; representative PNG and PDF files were fetched as base64 and confirmed to contain Git LFS pointer text (version URL, SHA-256 OID and original size).
- Extension distribution among these small pointer candidates: png: 381, pdf: 4, psd: 2, jpg: 4, bytes: 1, fbx: 3, wav: 22.
- This confirms that the small GitHub tree sizes are pointer blobs, not proof of broken image/PDF files.
- The current tree also contains 7 very large executable files (about 24–101 MB each) under `Game/Unity/FragmentosDoAmanha/Packages/com.unity.ai.assistant/RelayApp~/`. These are not covered by the listed LFS extension rules. Do not delete or relocate them independently; inspect the embedded package's purpose, package manifest and tracking policy before deciding whether they belong in the repository.
- GitHub tree lists 3,463 `.meta` files and 2,014 `.cs` files. Unity metadata preservation is a hard requirement.
- .gitattributes configures LFS, but it does not prove that Git LFS is installed and functioning on the user's production workstation. That must be checked locally before bulk binary moves.

## Safety findings
- The repository tree was not truncated during inventory.
- No production files were moved or deleted during this inventory.
- The actual LFS object availability and local checkout integrity still need verification on the production workstation.
- The Unity project must remain at `Game/Unity/FragmentosDoAmanha/` until the isolated relocation phase is approved and tested.

## Next checks
1. On the production workstation, run `git lfs version`, `git lfs ls-files` and `git lfs fsck`.
2. Confirm LFS objects can be fetched and the sample PNG/PDF files open normally.
3. Inspect the AI Assistant embedded relay binaries and package manifest.
4. Capture Unity GUID baseline and run an Editor validation before and after project relocation.


## Post-migration note — 2026-11-16

The original inventory above is retained as a historical baseline. The complete Unity project subtree was relocated to `Game/Unity/FragmentosDoAmanha/` by reusing its original tree SHA. Its 6,628 file blobs and 3,463 `.meta` files remain unchanged. Local Git LFS object verification and Unity Editor smoke tests are still required.
