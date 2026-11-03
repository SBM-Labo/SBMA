# Third-Party Notices — SportsBioMechanicsAnalyzer

SportsBioMechanicsAnalyzer（以下「本ソフトウェア」）本体には、利用規約（`LICENSE.txt`）が適用されます。
本ソフトウェアの配布物（インストーラー）には、以下の第三者ソフトウェア・移植コード・学習済みモデルが含まれます。
各コンポーネントには、本ソフトウェアの利用規約ではなく、それぞれのライセンスが優先して適用されます。
ライセンス全文は同梱の `licenses/` フォルダにあります。

SportsBioMechanicsAnalyzer itself is governed by its Terms of Use (`LICENSE.txt`). The distribution includes the third-party
software, ported source code and pretrained models listed below. Each component is governed by its own license, which takes
precedence over the Terms of Use of this software. Full license texts are in the `licenses/` folder.

| ファイル / File | 内容 / Contents |
|---|---|
| `licenses/MIT.txt` | MIT ライセンスの各コンポーネント（著作権表示＋許諾文） |
| `licenses/BSD-3-Clause.txt` | BSD ライセンスの各コンポーネント（原文のまま） |
| `licenses/ISC.txt` | ISC ライセンスの各コンポーネント（原文のまま） |
| `licenses/Apache-2.0.txt` | Apache License 2.0 |
| `licenses/GPL-3.0.txt` | GNU General Public License v3 |
| `licenses/LGPL-2.1.txt` | GNU Lesser General Public License v2.1 |
| `licenses/LGPL-3.0.txt` | GNU Lesser General Public License v3 |
| `licenses/OpenCV-3rdparty-macOS.txt` | macOS 版に静的リンクした libjpeg-turbo・libpng・zlib のライセンス（原文のまま） |

---

## 1. 別プロセスとして起動する実行ファイル / Separate executables (FFmpeg)

FFmpeg / FFprobe は本ソフトウェアとは独立したプログラムとして同梱し、**別プロセスとして**（コマンドライン引数を渡して）起動します。
本ソフトウェアのコードは FFmpeg のライブラリとリンクしていません。

FFmpeg and FFprobe are shipped as independent programs and are executed **as separate processes** (command-line invocation).
The code of this software is not linked with the FFmpeg libraries.

| 実行ファイル | 同梱元 npm パッケージ | ビルド | ライセンス | 対応ソースコード |
|---|---|---|---|---|
| ffmpeg.exe（Windows x64） | `ffmpeg-static` 5.3.0（バイナリリリース `b6.1.1`） | FFmpeg **6.1.1** essentials build（www.gyan.dev, `--enable-gpl --enable-version3`） | GPL-3.0-or-later | https://github.com/FFmpeg/FFmpeg/commit/e38092ef93 |
| ffmpeg（macOS arm64） | `ffmpeg-static` 5.3.0（バイナリリリース `b6.1.1`） | FFmpeg **6.0**（osxexperts.net build, `--enable-gpl --enable-version3`） | GPL-3.0-or-later | https://ffmpeg.org/releases/ffmpeg-6.0.tar.xz |
| ffprobe.exe（Windows x64） | `@ffprobe-installer/win32-x64` 5.1.0 | FFmpeg git-2296078397（2023-02-13）essentials build（www.gyan.dev, `--enable-gpl --enable-version3`） | GPL-3.0-or-later | https://github.com/FFmpeg/FFmpeg/commit/2296078397 |
| ffprobe（macOS arm64） | `@ffprobe-installer/darwin-arm64` 5.0.1 | FFprobe **n4.4.1**（GPL 部分を含まない LGPL ビルド） | LGPL-2.1-or-later | https://ffmpeg.org/releases/ffmpeg-4.4.1.tar.xz |

- npm パッケージ `ffmpeg-static`（ラッパー JS）は GPL-3.0-or-later、`@ffprobe-installer/ffprobe`（ラッパー JS）は LGPL-2.1 です。
- Windows 版のビルド構成・同梱ライブラリ（x264, x265, libvpx, libaom ほか）は https://www.gyan.dev/ffmpeg/builds/ に公開されています。
- 各バイナリのバージョンとビルド構成は、同梱の実行ファイルに `-version` を付けて実行すると確認できます（アプリの「ヘルプ → 診断情報をコピー」にも表示されます）。

**ソースコードの提供（書面による申し出） / Written offer for source code**
上記 GPL / LGPL のプログラムの対応するソースコード（FFmpeg 本体）は、表の「対応ソースコード」の入手先で公開されています。各ビルドに含まれるライブラリのソースとビルド設定は、上記のビルド提供元で公開されています。
入手できない場合は、本ソフトウェアの配布日から少なくとも3年間、作者（Kazutaka Murata <k-murata@andrew.ac.jp>）に連絡いただければ、
複製・送付の実費を超えない費用で、媒体またはダウンロードにより提供します。
For the GPL/LGPL programs above, the corresponding source code of FFmpeg is available from the locations in the table, and the sources
and build configurations of the bundled libraries are published by the build providers listed above. For at least three years from the date of distribution, the author will also provide it on request (k-murata@andrew.ac.jp) for no
more than the cost of physically performing the source distribution.

---

## 2. アプリケーション基盤・npm パッケージ / Application runtime and npm packages

| コンポーネント | 版 | ライセンス | 著作権表示 / Copyright |
|---|---|---|---|
| Electron | 44.5.1 | MIT | Copyright (c) Electron contributors; Copyright (c) 2013-2020 GitHub Inc. |
| Chromium（Electron に内蔵） | 152 | BSD-3-Clause ほか多数 | The Chromium Authors ほか。インストール先の `LICENSES.chromium.html`（Electron 同梱）に全ライセンスを収録 |
| Node.js（Electron に内蔵） | 24 | MIT ほか | Copyright Node.js contributors（同梱ライブラリを含む全文: https://github.com/nodejs/node/blob/main/LICENSE） |
| three.js（`app/renderer/lib/three.module.js`, `OrbitControls.js` として同梱） | r153 | MIT | Copyright © 2010-2023 three.js authors |
| ONNX Runtime（`onnxruntime-node`, `onnxruntime-common`） | 1.23.2 | MIT | Copyright (c) Microsoft Corporation |
| DirectML.dll / dxcompiler.dll / dxil.dll（Windows。`onnxruntime-node` に同梱の GPU 推論用ランタイム） | — | Microsoft の再頒布条件に従う（dxcompiler は DirectX Shader Compiler: University of Illinois/NCSA ライセンス） | Copyright (c) Microsoft Corporation |
| math.js（`mathjs`） | 11.12.0 | Apache-2.0 | Copyright (C) 2013-2023 Jos de Jong（NOTICE は下記） |
| jpeg-js | 0.4.4 | BSD-3-Clause | Copyright (c) 2014, Eugene Ware |
| mathjs の依存: complex.js, decimal.js, escape-latex, fraction.js, javascript-natural-sort, seedrandom, tiny-emitter, typed-function, @babel/runtime | — | MIT | 各著作権者（`licenses/MIT.txt`） |
| onnxruntime-node の依存: adm-zip, global-agent, roarr, sprintf-js, serialize-error, matcher, boolean ほか | — | MIT / BSD-3-Clause / ISC | 各著作権者（`licenses/MIT.txt`, `BSD-3-Clause.txt`, `ISC.txt`） |
| ffmpeg-static の依存: @derhuerst/http-basic, https-proxy-agent, env-paths, progress, debug, readable-stream ほか | — | MIT / BSD / ISC / Apache-2.0（caseless） | 各著作権者（同上） |
| type-fest | 0.13.1 | MIT OR CC0-1.0 | Copyright (c) Sindre Sorhus |

math.js の NOTICE（Apache-2.0 §4(d) による再掲）:

```
math.js
https://github.com/josdejong/mathjs

Copyright (C) 2013-2023 Jos de Jong <wjosdejong@gmail.com>

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```

---

## 3. OpenCV（Windows 版の DLL／macOS 版の静的リンク） / OpenCV (Windows DLLs / macOS static linking)

ChArUco ボード検出・単眼内部校正・ステレオ校正は、本ソフトウェアのネイティブアドオン `opencv_module.node`（本ソフトウェアのコード）が
OpenCV を**動的リンク**して実行します。Windows 版は vcpkg でビルドした OpenCV と依存 DLL をインストール先の `resources/opencv/` に同梱します。

| コンポーネント | ライセンス |
|---|---|
| OpenCV 4（core, imgproc, imgcodecs, videoio, calib3d, features2d, flann, objdetect, dnn, aruco の `opencv_*4.dll`） | Apache-2.0 |
| libjpeg-turbo（jpeg62） | IJG / BSD-3-Clause / Zlib |
| libpng | libpng License |
| libtiff | libtiff License |
| libwebp / libsharpyuv | BSD-3-Clause |
| zlib | Zlib |
| liblzma (XZ Utils) | 0BSD / Public Domain |
| Protocol Buffers | BSD-3-Clause |
| Abseil | Apache-2.0 |
| Microsoft Visual C++ ランタイム（msvcp140, vcruntime140, vcruntime140_1, concrt140） | Microsoft Visual Studio のライセンス条項に基づく再頒布可能コード（Redistributable） |

各ライブラリのライセンス全文は vcpkg の各ポート（`installed/x64-windows/share/<port>/copyright`）に含まれます。
Visual C++ ランタイムは、利用者の PC に Visual C++ 再頒布可能パッケージが入っていなくても ChArUco 機能が動くよう、`resources/opencv/` に同梱しています。

**Qt 5 について（LGPL-3.0）:** v1.3 までの Windows 版は、OpenCV の highgui モジュールが依存する Qt 5
（Qt5Core / Qt5Gui / Qt5Widgets / Qt5Concurrent / Qt5DBus / Qt5Network / Qt5OpenGL / Qt5PrintSupport / Qt5Sql / Qt5Test）と
その依存ライブラリ（OpenSSL, FreeType, HarfBuzz, PCRE2, double-conversion, Brotli, bzip2 ほか）を同梱していました。
v1.4.0 ではネイティブアドオンを highgui なしで再ビルドし、**Qt 5 の DLL（`Qt5*.dll`）と `opencv_highgui*.dll` は同梱しません**。
これらを同梱した版（v1.3 以前）では、Qt 5 は LGPL-3.0（`licenses/LGPL-3.0.txt`, `licenses/GPL-3.0.txt`）に基づき動的リンクで利用しており、
利用者は互換の DLL に差し替えることができます。Qt 5 のソースコード: https://download.qt.io/archive/qt/5.15/

### macOS 版 / macOS

macOS 版は、OpenCV 4.13.0（opencv の core, imgproc, imgcodecs, videoio, calib3d, features2d, flann, objdetect と opencv_contrib の aruco）を
ソースから静的ライブラリとしてビルドし、ネイティブアドオン `opencv_module.node` に**静的リンク**しています（OpenCV の共有ライブラリは同梱しません）。
画像の読み書きには OpenCV に同梱の libjpeg-turbo・libpng・zlib を使い、動画の読み込みには macOS 標準の AVFoundation を使います（OpenCV に FFmpeg は組み込んでいません）。

The macOS version statically links OpenCV 4.13.0 (the modules listed above and the aruco module of opencv_contrib) and the bundled
libjpeg-turbo, libpng and zlib into the native add-on `opencv_module.node`. Video is read through the macOS AVFoundation framework.

| コンポーネント | 版 | ライセンス |
|---|---|---|
| OpenCV / opencv_contrib（aruco） | 4.13.0 | Apache-2.0（`licenses/Apache-2.0.txt`） |
| libjpeg-turbo | 3.1.2 | IJG / BSD-3-Clause / Zlib |
| libpng | 1.6.53 | libpng License |
| zlib | 1.3.1 | Zlib |

libjpeg-turbo・libpng・zlib のライセンス全文は `licenses/OpenCV-3rdparty-macOS.txt` にあります。
This software is based in part on the work of the Independent JPEG Group.

---

## 4. 本ソフトウェアに含まれる移植コード / Ported source code included in this software

| 対象ファイル | 元のソフトウェア | ライセンス | 著作権表示 / 備考 |
|---|---|---|---|
| `modules/hpe/node_inference/lib/bytetrack.js` | ByteTrack（ifzhang/ByteTrack: `byte_tracker.py`, `kalman_filter.py`, `matching.py`）の JavaScript 移植 | MIT | Copyright (c) 2021 Yifu Zhang |
| `modules/hpe/node_inference/lib/simcc.js`, `decode.js`, `imgproc.js`, `pipeline.js`（SimCC デコード・DARK/UDP 後処理・前処理） | rtmlib（Tau-J/rtmlib）のアルゴリズムの JavaScript 移植（変更あり） | Apache-2.0 | rtmlib の LICENSE: "Copyright 2018-2020 Open-MMLab." — https://github.com/Tau-J/rtmlib |

| `app/assets/opensim/`（`Model_Pose2Sim_simple.osim`、`Model_Pose2Sim_muscles_flex.osim`、`Markers_Halpe26.xml`、`Markers_LSTM.xml`、Scaling/IK の設定 XML。OpenSim 書き出しで同梱・コピー） | Pose2Sim（perfanalytics/pose2sim, `Pose2Sim/OpenSim_Setup`） | BSD-3-Clause | Copyright (c) 2022, perfanalytics。ライセンス全文は `app/assets/opensim/LICENSE_Pose2Sim.txt`（書き出しフォルダにも同梱）。`Markers_LSTM.xml` のマーカー名は OpenCap（stanfordnmbl/opencap-core, Apache-2.0）のマーカーセットに由来 |

Python の rtmlib / MMPose 自体は同梱・使用していません（アルゴリズムのみ移植）。

3次元CC法（`modules/motiondigitizer/src/cc-calibration.js`）は、下記の論文に書かれた手法をもとにした独自の実装で、第三者のコードは含みません。 / The 3D CC-method calibration (`modules/motiondigitizer/src/cc-calibration.js`) is an independent implementation based on the published description of the method below and contains no third-party code.

- 手法の出典 / Method: Suzuki, Y., Takenaka, S., Enomoto, Y., Tauchi, K. (2016) A study on the calculation of the camera parameters using feature points on the field. Japanese Journal of Biomechanics in Sports and Exercise, 20(1), 2–9.

---

## 5. 学習済みモデル / Pretrained models

モデルファイルはインストーラーに同梱しています。 / The model files are bundled with the installer.

| ファイル | 用途 | 出典 | ライセンス | 著作権表示 | サイズ / SHA-256 |
|---|---|---|---|---|---|
| `rfdetr-medium.onnx` | 人物・ボールの検出（RF-DETR-M, COCO 学習済み） | Roboflow RF-DETR（https://github.com/roboflow/rf-detr） | Apache-2.0 | Copyright 2025 Roboflow, Inc. | 129,389,086 B / `e715c80812d004fcbd52ca61cecaceba8f31f6368ec4ec74f6a81f44827841c5` |
| `rtmpose-m.onnx` | 全身姿勢推定（RTMPose-m） | OpenMMLab MMPose（https://github.com/open-mmlab/mmpose） | Apache-2.0 | Copyright 2018-2020 Open-MMLab | 55,685,444 B / `26f3a19e61304a600dfb82d1001d41d24343b89fc70a33ffc84657e0b0bf2ecf` |
| `rtmpose-m_hand.onnx` | 手部姿勢推定（RTMPose-m hand） | OpenMMLab MMPose | Apache-2.0 | Copyright 2018-2020 Open-MMLab | 55,080,248 B / `39e858936bca0f94c09847d4e70b68a51d6c0adac61f36b457fcadb54621cd29` |

- 各モデルは原配布の重みを ONNX 形式に変換したものです（重みの変更なし）。RF-DETR は Nano〜Large の検出モデルが Apache-2.0 で公開されています（XL/2XL は別ライセンスで、本ソフトウェアでは使用していません）。
- モデルの学習に用いられたデータセット（COCO ほか）の利用条件は、各データセットの提供元の定めに従います。

---

## 6. 数値データ（引用） / Data tables (cited)

身体部分慣性係数（BSP）の係数表は、以下の文献の公表値を引用しています（`app/shared/body-com.mjs`）。

- 阿江通良・湯海鵬・横井孝志 (1992) 日本人アスリートの身体部分慣性特性の推定. バイオメカニズム, 11, 23–33.（成人：阿江14/15）
- 岡田英孝・阿江通良・藤井範久・森丘保典 (1996) 日本人高齢者の身体部分慣性特性. バイオメカニズム, 13, 125–139.（高齢者：岡田14）
- 横井孝志・渋川侃二・阿江通良 (1986) 日本人幼少年の身体部分係数. 体育学研究, 31(1), 53–66.（小児：横井）
