# runner-comfyui

GPU Runner Agent Image for ComfyUI.

## GHCR mirror

This repo republishes `oci.offloadr.app/runner/nvidia:latest` to:

`ghcr.io/offloadr/runner-nvidia:latest`

The mirror workflow lives at `.github/workflows/republish-runner.yml` and runs:

- on manual dispatch
- daily at `03:17 UTC`
- on pushes to `main`

The workflow:

- installs `skopeo`
- logs in to `ghcr.io` with `GITHUB_TOKEN`
- copies the image with `skopeo copy --all`
- compares source and destination digests after the copy

After the first successful publish, the GHCR package will exist under the `offloadr`
owner as `runner-nvidia`. If you want anonymous pulls, change the package visibility
to public in GitHub package settings after that first push.
