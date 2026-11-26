# Creatorize Assets

Essential scene props library for Creatorize / Claude / three.js renders — house, city, infrastructure, nature, vehicles and city props.

- **1,375 props, 16.53 GB** (16,926.58 MB)
- Categories: Animal 107, Building 220, Character 126, Container 13, Decoration 16, Electronics 80, Food 56, Furniture 58, Gym 46, Household 9, Military 2, Music 41, Nature 138, Prop 216, Sci-Fi 1, Sculpture 40, Tool 6, Vehicle 145, Weapon 54, Western 1
- Format: GLB (`.glb`); small files are regular git blobs, large files are stored with Git LFS
- Files live under `props/<category>/<filename>.glb`
- Full index: `props-index.json` (name, category, size_mb, sha256, github_path, batch)

## How Claude clones it

```bash
git clone --depth 1 https://github.com/unknowjason20-cloud/creatorize-assets.git
cd creatorize-assets
git lfs pull --include "props/<category>/<filename>.glb"
```

Or fetch a single file without cloning the whole 16.53 GB:

```bash
git clone --filter=blob:none --no-checkout https://github.com/unknowjason20-cloud/creatorize-assets.git
cd creatorize-assets
git sparse-checkout set props/<category>
git checkout
git lfs pull --include "props/<category>/<filename>.glb"
```

## Notes

- Every `.glb` is tracked with Git LFS in `.gitattributes` (`*.glb filter=lfs diff=lfs merge=lfs -text`), but files uploaded via the GitHub API as regular blobs still work — git-lfs passes them through unchanged (content-based smudge), so the repo mixes regular + LFS `.glb` files. A single file is at most 265 MB; GitHub LFS allows up to 2 GB per file.
- Upload history: V2 (719 props, 5 LFS batches) + V3 (656 props: 615 regular API blobs + 41 LFS files). The web UI refuses `.glb` uploads while `.gitattributes` marks them as LFS — API upload only.
- The `sha256` in `props-index.json` is the hash of the GLB file itself (for LFS files, the hash of the real GLB, not the pointer).
