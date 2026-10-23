# Nativos Audio — Plugin Updates

This is the **public download and update-information repository** for Nativos Audio plugins. It is separate from the private source-code repository.

## Nativos Soft Clipper

- **Stable update feed:** [updates/softclipper/stable.json](updates/softclipper/stable.json) (appears after the first approved public release)
- **Installer downloads:** [Releases](https://github.com/tolynativo/nativos-audio-updates/releases)
- **Supported formats:** macOS VST3 and AU; Windows VST3.
- **Update behavior:** updater-enabled plugins can check this stable feed, display version notes, download the appropriate installer over HTTPS, and verify the SHA-256 checksum.
- **Install safety:** close your DAW before installing. The plugin never runs installers automatically.

## How releases are published

Installers are built and reviewed in the **private** NativosOptoOne repository. For the first release, the approved Mac and Windows installers can be uploaded using GitHub's **Releases** page without creating another access token. A workflow in this **public** repository then publishes the SHA-256-verified stable update feed using GitHub's built-in permissions. See [simple release instructions](RELEASING.md).

No plugin source, signing identities, or private credentials belong in this public repository.

> **Status:** The public repository is ready. The update feed becomes live after the first approved Mac and Windows release is published. Until then, the installed plugin may say that updates are unavailable. Builds and installers still require DAW verification, and unsigned packages may show operating-system security warnings.
