# PeezJob FFmpegKitNext build source

This repository records the FFmpegKitNext source pin and local build steps for PeezJob's Android and iOS binaries.

The `ffmpeg-kit-next` submodule points to upstream commit `5e51b2da4c3593c0f2f9b49f53eeb497d93e39d3`. Clone this repository with `--recurse-submodules` to get that source.

This repository has build instructions, one shared source pin patch, and one Android patch. It has no PeezJob app code, credentials, or built binaries. It does not include PeezJob's private CI workflow or internal runbook.

The build enables GNU General Public License (GPL) components and x264. FFmpegKitNext states that these bundles use GPL version 3 (GPLv3). The build source pins each fetched dependency to a commit. The upstream source and each dependency keep their own license and notices.

Copyright (c) 2026 VelocityCubed. VelocityCubed-authored files in this repository are licensed under GPL-3.0-only. This includes the build instructions, source metadata, and patches. The license does not change the terms for the `ffmpeg-kit-next` submodule or fetched third-party source. See [LICENSE](LICENSE) and [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md).

See [BUILDING.md](BUILDING.md) for local commands. See [SOURCE-PIN.json](SOURCE-PIN.json) for the source commits, patches, and build options.
