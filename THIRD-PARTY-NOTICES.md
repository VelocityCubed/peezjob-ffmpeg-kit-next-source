# Third-party notices

This file records the native source components selected by the build options in `SOURCE-PIN.json`. It does not replace any notice in the upstream source. The `LICENSE` file applies only to VelocityCubed-authored files in this repository.

| Component | Platforms | Source revision | Source license and notice |
| --- | --- | --- | --- |
| FFmpegKitNext | Android, iOS | [`5e51b2da4c3593c0f2f9b49f53eeb497d93e39d3`](https://github.com/arthenica/ffmpeg-kit-next/commit/5e51b2da4c3593c0f2f9b49f53eeb497d93e39d3) | LGPL-3.0-or-later for the library source. See [`LICENSES/FFmpegKitNext-LICENSE.txt`](LICENSES/FFmpegKitNext-LICENSE.txt). The configured bundle is GPLv3 because the build enables GPL components. |
| FFmpeg | Android, iOS | [`bf1b838f2ab88b4f8fd83443325c782ea0e0f7fa`](https://github.com/arthenica/FFmpeg/commit/bf1b838f2ab88b4f8fd83443325c782ea0e0f7fa) | GPLv3 in this build configuration. See [`LICENSES/GPL-3.0.txt`](LICENSES/GPL-3.0.txt). |
| x264 | Android, iOS | [`b35605ace3ddf7c1a5d67a2eb553f034aef41d55`](https://github.com/arthenica/x264/commit/b35605ace3ddf7c1a5d67a2eb553f034aef41d55) | GPL-2.0-or-later in the upstream source. See [`LICENSES/x264-COPYING-GPL-2.0.txt`](LICENSES/x264-COPYING-GPL-2.0.txt). |
| cpu_features | Android | [`81d13c49649f0714dd41fb56bb246398b6584085`](https://github.com/arthenica/cpu_features/commit/81d13c49649f0714dd41fb56bb246398b6584085) | Apache-2.0. The `ndk_compat` files also carry a BSD-style notice. See [`LICENSES/cpu_features-LICENSE-Apache-2.0.txt`](LICENSES/cpu_features-LICENSE-Apache-2.0.txt), which preserves both notices. The pinned source revision has no separate `NOTICE` file. |

The build also retrieves GNU config and the iOS `gas-preprocessor.pl` helper. Their exact source commits are recorded in `SOURCE-PIN.json`. They are build inputs and are not listed above as native libraries in the output bundle.

This notice covers the components selected by the recorded build flags. Review the actual build configuration and generated license notices before publishing each binary version. Preserve the linked source revisions and these license texts with the corresponding release.
