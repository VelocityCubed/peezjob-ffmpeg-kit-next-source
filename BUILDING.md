# Build locally

## Requirements

- Git with submodule support.
- Nix with the `nix-command` and `flakes` features.
- For iOS: macOS with Xcode 26 at `/Applications/Xcode.app`.
- For Android: Java Development Kit (JDK) 17.

The build uses Nix profiles and source inputs from the pinned FFmpegKitNext revision. Its scripts retrieve the required dependency sources.

## Get the pinned source

Clone this repository with its submodule:

```sh
git clone --recurse-submodules https://github.com/VelocityCubed/peezjob-ffmpeg-kit-next-source.git
cd peezjob-ffmpeg-kit-next-source
```

Check the source pin:

```sh
git -C ffmpeg-kit-next rev-parse HEAD
```

It must print:

```text
5e51b2da4c3593c0f2f9b49f53eeb497d93e39d3
```

## Apply the source pins

Apply this patch once before either platform build. It changes upstream dependency fetches to use the commits in `SOURCE-PIN.json`.

```sh
git -C ffmpeg-kit-next apply --check ../patches/0002-pin-build-source-commits.patch
git -C ffmpeg-kit-next apply ../patches/0002-pin-build-source-commits.patch
```

## Build Android

Apply the Android patch once:

```sh
git -C ffmpeg-kit-next apply --check ../patches/0001-android-suppress-unused-function-warning.patch
git -C ffmpeg-kit-next apply ../patches/0001-android-suppress-unused-function-warning.patch
```

Build the Android AAR:

```sh
cd ffmpeg-kit-next
nix --extra-experimental-features 'nix-command flakes' develop .#android-r27d -c ./nix-android.sh \
  -p android-r27d \
  --enable-gpl \
  --enable-x264 \
  --enable-android-media-codec \
  --no-ffmpeg-kit-protocols
```

## Build iOS release frameworks

From the repository root, run:

```sh
cd ffmpeg-kit-next
nix --extra-experimental-features 'nix-command flakes' develop .#xcode26 -c ./nix-ios.sh \
  -p xcode26 \
  -x \
  --enable-gpl \
  --enable-x264 \
  --enable-ios-videotoolbox \
  --no-ffmpeg-kit-protocols \
  --disable-arm64-mac-catalyst \
  --disable-x86-64-mac-catalyst \
  --disable-arm64-simulator \
  --disable-x86-64
```

## Build iOS development frameworks

From the repository root, run:

```sh
cd ffmpeg-kit-next
nix --extra-experimental-features 'nix-command flakes' develop .#xcode26 -c ./nix-ios.sh \
  -p xcode26 \
  -x \
  --enable-gpl \
  --enable-x264 \
  --enable-ios-videotoolbox \
  --no-ffmpeg-kit-protocols \
  --disable-arm64-mac-catalyst \
  --disable-x86-64-mac-catalyst
```

The scripts write output under `prebuilt/` inside the upstream source directory. The iOS release build is device-only. The development build also includes simulator slices.

## Source and changes

The submodule points to the exact FFmpegKitNext commit used for the producer build. The source pin patch makes the build scripts fetch FFmpeg, x264, Android CPU features, GNU config, and the iOS build helper from recorded commits. `SOURCE-PIN.json` records each commit and the iOS helper checksum. The Android patch is stored in this repository.

This repository links to the upstream dependency commits; it does not mirror their source archives. Keep these public source references available while you offer binaries built from them. Apply the source pin patch before each platform build. The iOS and Android patch requirements are listed above.
