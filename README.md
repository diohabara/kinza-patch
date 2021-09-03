# kinza 6.9.0 build method

## Distribution

- args.gn: The settings file used for the build
- kinza_6.9.0.patch: The patch file (*) for kinza 6.9.0
- LICENSE.txt: The file containing the license information
- README.ja.md: The Japanese version for README.md
- README.md: This file

(*) More precisely, this is not a patch file for kinza 6.9.0. This patch does not include the video playback feature developed by Dayz Inc. It also does not include the installer feature.

## Preconditions

To build kinza 6.9.0 with the distributed patch files, you need to be able to build chromium 89.0.4389.128　(chromium's source code git hash value: ```cd7a46bf02a768a1aabf9443f6ee469bc6e28e7c``` ). Ensure you can build chromium 89.0.4389.128 beforehand. See the following URL for information on chromium builds.

https://www.chromium.org/developers/how-tos/get-the-code


## Environment confirmed build

We have used this patch to confirm the kizna 6.9.0 build.

### Windows

- Windows 10 20H2
- Windows 10 SDK: 10.0.19041
- Visual Studio Community 2019 Version 16.4.4
- gclient's git hash value: b3c9edb4af40cce0512adbcae7fc3fd2450e2b45

### Mac

- MacOS 11.4
- Xcode 12.2
- macOS 11.0 SDK
- gclient's git hash value: 61bf6e8d69c4cb084b1541a996fc3f4990cd2535

## Build

The chromium 89.0.4389.128 source code is under Chromium/src below, with the current directory set to Chromium/src. Execute using the command prompt on Windows, and the terminal on Mac. Change the '\' to '/' on Mac.

```
git apply kinza_6.9.0.patch
gclient sync -D --with_branch_heads
gn gen out\Default
Place args.gn directly below out\Default
gn gen out\Default
autoninja -C out\Default chrome
```

## Execute

### Windows

When your build is successful, ```chrome.exe``` will be generated under ```out\Default```. Double click it.

### Mac

When your build is successful, ```Kinza.app``` will be generated under ```out\Default```. Double click it.