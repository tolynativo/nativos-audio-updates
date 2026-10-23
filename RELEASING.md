# Release Nativos Soft Clipper without a personal access token

This public repository hosts customer installers and update information. The plugin source remains private in `tolynativo/NativosOptoOne`.

## First public v2.6.0 update: easy manual upload

You **do not need to create or edit a personal access token**.

1. Obtain the two **approved v2.6.0** installer files from the completed private Mac and Windows builds:
   - `NativosSoftClipper-v2.6-macOS-Unsigned.pkg`
   - `NativosSoftClipper-v2.6-Windows-Unsigned-Setup.exe`
2. Open **https://github.com/tolynativo/nativos-audio-updates/releases/new**.
3. Set **Choose a tag** to `v2.6.0` and select **Create new tag on publish** on `main`.
4. Set the release title to `Nativos Soft Clipper v2.6.0`.
5. Paste accurate release notes mentioning the four new converter-inspired presets and renamed factory sounds.
6. Drag **both approved installers** into the **Attach binaries** area.
7. Confirm both filenames appear in the attachments, leave **pre-release** unchecked, then click **Publish release**.

GitHub will automatically run [Activate Nativos Soft Clipper public update feed](.github/workflows/activate-softclipper-update.yml) using its **built-in GITHUB_TOKEN** from this public repository. That workflow:
- checks that both public files exist and are not suspiciously small
- downloads them and calculates their exact SHA-256 hashes
- writes `updates/softclipper/stable.json` to `main`
- includes the exact platform-specific GitHub Releases URLs and version `2.6.0`

Customers running updater-enabled older versions can then check for v2.6.0 within their plugin. No installer runs itself. Customers already on v2.6.0 will correctly see that they are up to date.

## Check that the update is live

1. Check the [public release](https://github.com/tolynativo/nativos-audio-updates/releases/tag/v2.6.0) has **two** downloadable assets.
2. Open the [Actions page](https://github.com/tolynativo/nativos-audio-updates/actions/workflows/activate-softclipper-update.yml) and confirm the activation run succeeds.
3. Open [stable.json](https://raw.githubusercontent.com/tolynativo/nativos-audio-updates/main/updates/softclipper/stable.json) and confirm `version` is `2.6.0` and both URLs and SHA-256 hashes exist.
4. Test the plugin's **UPDATES** panel with a v2.5.0 install and verify it offers v2.6.0. Confirm both installer downloads and checksums.

If the workflow errors on a permissions message, open **Settings > Actions > General > Workflow permissions** in the **public** repository and allow Read and write permissions if the organization or account policy permits. The workflow explicitly requests `contents: write`.

## Important

Both current installers are unsigned. For broad public deployment, sign/notarize the macOS package and code-sign the Windows installer, then update release assets and regenerate the feed so hashes still match. Changes to installer bytes after publishing require updated SHA-256 hashes. Preserve VST3/AU plugin identifiers, audio project recall, and customer presets.

For future versions, repeat the release upload and update the workflow's approved tag, filenames and release notes; a dedicated automated pipeline can be added later if cross-repository credentials become available.
