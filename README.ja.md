# Erduo B-roll Loop Engineering

**原本の SRT とデザインから、意味のある動きと編集可能なソースを備えた B-roll を制作します。**

[简体中文](README.md) · [English](README.en.md) · 日本語 · [한국어](README.ko.md) · [繁體中文](README.zh-TW.md)

> `main` は映像品質を優先する役割分担方式です。最新の番号付き Release は [v1.0.1](https://github.com/erduo1998-cell/erduo-broll-loop-engineering/releases/tag/v1.0.1) のままで、その配布アーカイブは旧方式です。新方式は現在のリポジトリからインストールしてください。

## 制作の流れ

原本 SRT・デザイン・任意の素材 → 独立したディレクター → 新しいコンテキストの章別制作者 → スクリプトによるレンダリングと独立した映像レビュー → 元の制作者による部分修正 → 完成ショット・全体プレビュー・編集可能なプロジェクト。

短編でも演出・制作・審美レビューのコンテキストを分離します。各制作者には原本全体、短い共通方針、担当ショットと前後の接続情報を渡し、親の会話履歴や全 Skill は渡しません。長編は物語の連続性に沿って分担し、素材担当は必要な場合に追加します。

時間検査、レンダリング、デコード、キャッシュと結合は親がスクリプトで実行します。映像を実際に見て修正し、技術検査の成功を審美合格とみなしません。必要な試作や修正を時間・Token のために省略しません。ユーザー指定の確認・停止点は守ります。

3つの短い動きの参考と実行可能なオリジナル例を用意しています。色や紙のカードに固定するテンプレートではありません。対象を認識できる素材を使い、SVG は明確な関係・図表・マスク・パスに活用します。

## インストール

```sh
git clone https://github.com/erduo1998-cell/erduo-broll-loop-engineering.git
cd erduo-broll-loop-engineering
./Install.command
```

固定版 HyperFrames、ブラウザー、FFmpeg と Skill リンクを準備します。インストール先は保持し、完了後 Codex または Claude Code を再起動してください。v1.0.1 アーカイブを使う場合は同梱 README に従います。

```sh
node scripts/doctor.mjs
node scripts/uninstall.mjs
```

アンインストールは既定でユーザーデータを保持します。

## 最初の依頼

```text
この原本 SRT とデザインから erduo-broll-loop-engineering で B-roll を制作してください。
ディレクター、章別制作者、映像レビュアーは別のコンテキストにしてください。
映像品質を優先し、実際の出力を確認・修正して全体プレビューを納品してください。
```

納品物は編集可能な HTML/CSS/JS、素材の出典、順序付き H.264 ショットと全体プレビューです。既定は無音 3840×2160・30fps。ユーザー指定を優先し、字幕全文や音楽は自動追加しません。

## 検証範囲

同一入力の32秒比較で、独立した Sol のキーフレーム・接続部分レビューは新方式を選び、ユーザーも採用しました。両作品は1080p/30fpsで実デコード済みです。S02 の変更は8.569秒で反映され、他の3ショットは同一のままでした。

**時間・Token 削減は未実証です。** モデル工程は新方式611.281秒、比較方式325.136秒でした。環境障害と無駄な検索を含むため、正確な総制作時間の比較ではありません。交接ツールは入力を整理しますが、ホストが追加する全コンテキストを削除したりサンドボックスを強制したりしません。[検証記録](docs/LEAN-WORKFLOW-VALIDATION.md)。

既存の Recipe/runtime-plan v1–v4 と明示的な Remotion/hybrid は[旧方式](erduo-broll-loop-engineering/references/legacy-production.md)を維持します。長編、Windows、編集ソフトの GUI、バックエンド間の見た目の一致は新方式で未検証です。152枚の Shotcraft カードは任意の参考であり、検証済みコンポーネント152個ではありません。

## 開発

```sh
npm test
npm run task:creative -- --project /path/to/project --role director
npm run render:lean -- --project /path/to/project --quality draft
```

[制作コマンド](erduo-broll-loop-engineering/references/lean-production.md) · [動きの参考](erduo-broll-loop-engineering/references/motion-patterns.md) · [プライバシー](PRIVACY.md) · [対応範囲](SUPPORT-MATRIX.md) · [更新履歴](CHANGELOG.md) · [MIT](LICENSE)
