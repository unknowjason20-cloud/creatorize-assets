# Creatorize Assets

Essential scene props library for Creatorize / Claude / three.js renders — house, city, infrastructure, nature, vehicles and city props.

- **719 props, 9.89 GB** (10,129.2 MB)
- Categories: Building 220, Vehicle 145, Nature 138, Prop 216
- Format: GLB (`.glb`), stored with Git LFS
- Files live under `props/<category>/<filename>.glb`
- Full index: `props-index.json` (name, category, size_mb, sha256, github_path, batch)

## How Claude clones it

```bash
git clone --depth 1 https://github.com/unknowjason20-cloud/creatorize-assets.git
cd creatorize-assets
git lfs pull --include "props/<category>/<filename>.glb"
```

Or fetch a single file without cloning the whole 9.89 GB:

```bash
git clone --filter=blob:none --no-checkout https://github.com/unknowjason20-cloud/creatorize-assets.git
cd creatorize-assets
git sparse-checkout set props/<category>
git checkout
git lfs pull --include "props/<category>/<filename>.glb"
```

## Notes

- Every `.glb` is tracked with Git LFS (`*.glb filter=lfs diff=lfs merge=lfs -text` in `.gitattributes`). A single file is at most 265 MB; GitHub LFS allows up to 2 GB per file.
- Uploaded in 5 batches of ~1.98 GB each (GitHub enforces a 2 GB push limit).
- Source: Sketchfab GLBs, no license found in the files — free to use everywhere per the project's Sketchfab rule. See `props-index.json` for the per-prop source list in the original library.
