# Site Asset Import

ChatGPT stages approved original website assets in the shared Google Drive bridge and records direct-download URLs plus integrity data in `pending.json`.

From the local checkout, Codex runs:

```bash
bash scripts/import-pending-assets
```

The importer downloads the complete pending batch, verifies byte size and SHA-256, writes the original bytes to their declared site paths, clears the manifest, commits, and pushes.
