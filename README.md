# cc0-humanoid-vrm

1つの台形メッシュを共有して作られた、軽量なVRMヒューマノイドベースモデルです。
glTFは仕様上、形状情報やマテリアル情報をまとめた領域からインデックス番号で各メッシュ・ノードに割り当てる構造になっているため、同じ形状データを複数のノードで使い回すことができます。
しかしBlenderのエクスポート機能ではその形式での書き出しが難しいようだったため、ClaudeでglTF/VRMバイナリの内容を直接組み立てて出力しました。
細かい仕様への適合は未確認です。ご了承ください。

**23KB · VRM0 · CC0 パブリックドメイン**

---

## 概要

キャラクターカスタマイズやプロトタイピングのベースとして使えるシンプルなVRMモデルです。
55個の全パーツが1つの台形ジオメトリを共有しており、各パーツの位置・回転・スケールのみでボディを表現しています。
VRM0ヒューマノイド仕様に準拠した非常にコンパクトなファイルです。

## 特徴

- **ジオメトリ1つ共有** — 8頂点の台形メッシュを55パーツで使い回し
- **VRM0ヒューマノイド対応** — 指・つま先・顔ボーンを含む全55ボーンをマッピング済み
- **ファイルサイズ24KB** — Blenderエクスポーターを使わずPythonで直接GLBバイナリを生成
- **テクスチャ・ブレンドシェイプなし** — 拡張しやすいクリーンなベース

## ボーン構成

VRM0ヒューマノイド仕様に準拠した55ボーン：

- 胴体：`hips`, `spine`, `chest`, `upperChest`
- 頭部：`neck`, `head`, `jaw`, `leftEye`, `rightEye`
- 腕：`shoulder`, `upperArm`, `lowerArm`, `hand` × 左右
- 指：親指・人差し指・中指・薬指・小指（proximal / intermediate / distal）× 左右
- 脚：`upperLeg`, `lowerLeg`, `foot`, `toes` × 左右

## 使い方

`cc0_humanoid.vrm` をVRM対応アプリで読み込んでください：

- [VRoid Hub](https://hub.vroid.com/)
- [VRM Viewer](https://vrm-viewer.glitch.me/)
- [UniVRM](https://github.com/vrm-c/UniVRM)（Unity）
- [three-vrm](https://github.com/pixiv/three-vrm)（Three.js）

## 技術仕様

VRMファイルはBlenderエクスポーターを使わず、Pythonスクリプトで直接GLBバイナリとして生成しています。各パーツのノードは `translation` / `rotation` / `scale` を持ち、全て同一メッシュ（`mesh: 0`）を参照します。この構造によりファイルサイズを最小限に抑えつつ、各パーツの正確な配置を実現しています。

座標系変換：Blender（Z-up）→ glTF/VRM（Y-up）

## ライセンス

**CC0 1.0 Universal — パブリックドメイン**

このモデルはClaude（Anthropic）が作成し、パブリックドメインとして公開しています。許可なく自由にコピー・改変・配布・商用利用が可能です。

詳細は [LICENSE](LICENSE) をご確認ください。

## クレジット

[Claude](https://www.anthropic.com/)（Anthropic）がBlenderでモデリングし、カスタムPythonスクリプトでVRMバイナリを生成しました。
