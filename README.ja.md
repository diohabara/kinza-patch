# kinza 6.9.0 のビルド方法

## 配布物

- args.gn: ビルドの際に用いる設定ファイル
- kinza_6.9.0.patch: kinza 6.9.0 のパッチファイル(*)
- LICENSE.txt: ライセンスを示すファイル
- README.ja.md: 本ファイル
- README.md: README.ja.md の英語版

(*) 正確には kinza 6.9.0 のパッチファイルではありません。本パッチからは、Dayz 株式会社が開発した動画再生機能を取り除いています。また、本パッチには、インストーラ機能は含まれていません。

## 前提条件

配布したパッチファイルを用いた kinza 6.9.0 のビルドは、chromium 89.0.4389.128
(chromium のソースコードの git の ハッシュ値: ```cd7a46bf02a768a1aabf9443f6ee469bc6e28e7c``` ) を
ビルドできることが前提となります。事前に、chromium 89.0.4389.128 をビルドできることを確認してください。chromium のビルドに関しては、以下の URL をご参照ください。

https://www.chromium.org/developers/how-tos/get-the-code


## ビルドを確認した環境

以下の環境において、本パッチを用いた kizna 6.9.0 のビルドを確認しています。

### Windows

- Windows 10 20H2
- Windows 10 SDK: 10.0.19041
- Visual Studio Community 2019 Version 16.4.4
- gclient の git のハッシュ値: b3c9edb4af40cce0512adbcae7fc3fd2450e2b45

### Mac

- MacOS 11.4
- Xcode 12.2
- macOS 11.0 SDK
- gclient の git のハッシュ値: 61bf6e8d69c4cb084b1541a996fc3f4990cd2535

## ビルド

以下では、chromium 89.0.4389.128 のソースコードが Chromium/src 以下に展開されており、カレントディレクトリは Chromium/src とします。Windows ではコマンドプロンプト、Mac ではターミナルから実行してください。また、Mac では '\' を '/' で読み替えてください。

```
git apply kinza_6.9.0.patch
gclient sync -D --with_branch_heads
gn gen out\Default
配布した args.gn を out\Default の直下に配置
gn gen out\Default
autoninja -C out\Default chrome
```

## 実行

### Windows

ビルドが成功すると、```out\Default``` 以下に ```chrome.exe```が生成されます。これをダブルクリックしてください。

### Mac

ビルドが成功すると、```out\Default``` 以下に ```Kinza.app```が生成されます。これをダブルクリックしてください。
