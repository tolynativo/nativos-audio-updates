# Release process for Nativos Audio

This public repository serves installers and update metadata. Private plugin source stays in `tolynativo/NativosOptoOne`.

To connect publishing: on GitHub, create a fine-grained token that has Contents write access only to `tolynativo/nativos-audio-updates`. Add it to the private repository at Settings > Secrets and variables > Actions as `NATIVOS_PUBLIC_RELEASE_TOKEN`. Never paste credentials into a file or a chat.

Run the private repository's Soft Clipper build workflow on the `nativos-softclipper-updater` branch with publish unchecked first. Test installers in both DAWs. Update the source version, release notes and release workflow's currently hardcoded `RELEASE_VERSION` to the same approved release. Then run the workflow manually with publish enabled.

The publishing job will upload both installers to this public repository's Releases, calculate their SHA-256 hashes, and write `updates/softclipper/stable.json`. The plugin reads that feed to offer future updates. This feed should not exist until the first verified public release; never fill it with dummy installer links.

For public distribution, sign and notarize the Mac package and sign the Windows installer. Preserve product/plugin IDs and customer presets so previous projects continue working.
