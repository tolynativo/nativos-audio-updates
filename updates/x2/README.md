# X2 Compressor — Installer update feed

The X2 plugin's **Settings → Updates** panel reads [stable.json](stable.json). It downloads the installer into the user's **Downloads** folder, verifies the published SHA-256 checksum, and offers to reveal the downloaded file. It does **not** launch or silently install the package.

## Publishing an X2 release

1. Download the tested and approved macOS `.pkg` and Windows `.exe` build artifacts from the private `tolynativo/NativosOptoOne` `x2-compressor` branch.
2. Open **Releases → Draft a new release** in this *public* repository and attach both original installer files.
3. Choose a release tag beginning with `x2-v`, for example `x2-v0.7.1`. Publish when the installers are ready for customer distribution.
4. [Publish X2 verified installer update feed](../../.github/workflows/publish-x2-update.yml) will run after publication, verify file sizes, compute SHA-256 digests, and activate the public `stable.json` feed.
5. Test **CHECK FOR UPDATES → DOWNLOAD INSTALLER** on Mac and Windows. Confirm the installed version and a valid installer download.

The URL in the release feed points to a **direct installer asset**, never to the GitHub repository/release page. Customers do not need a GitHub login to download.

The feed starts with `published:false` and empty URLs. Until an approved public release is available, the plugin correctly reports that no verified installer has been published.

**Security:** Public installers should be signed before commercial distribution. Keep certificates, notarization credentials and source code in the private repository. Do not execute installer files automatically while a DAW has the plugin loaded.