# Erduo B-roll Loop Engineering

**把原始 SRT 與設計要求，做成有審美、有連貫動作、能繼續修改的 B-roll。**

[简体中文](README.md) · [English](README.en.md) · [日本語](README.ja.md) · [한국어](README.ko.md) · 繁體中文

> `main` 採用品質優先的角色接力流程。最新版本化 Release 仍為 [v1.0.1](https://github.com/erduo1998-cell/erduo-broll-loop-engineering/releases/tag/v1.0.1)，其中的舊安裝包不會隨 main 更新。新流程請從目前的儲存庫安裝。

## 製作流程

原始 SRT ＋ design ＋ 可選素材 → 獨立導演 → 新的章節製作上下文 → 腳本渲染與獨立審美看片 → 原製作角色定點修改 → 正式鏡頭、完整預覽與可編輯工程。

**畫面效果優先。** 短片也保留導演、製作、審美的獨立上下文。製作者收到完整原始輸入、精簡共用風格、本章鏡頭與相鄰接縫，不背著父級整段會話和全部 Skill 開工。長片依敘事分章，素材人員按實際需要加入。

時間檢查、渲染、解碼、快取與拼接由父級執行腳本。實際看片與必要返修不能因省 Token 被刪除，也不能以技術通過代替審美通過。新風格可先試代表片段，不固定樣片數量；保留使用者要求的審看與暫停點。

提供三種精簡動效參考與一個可執行原創範例，幫助表達狀態變化、分類分流與焦點接力，不強制紙片模板或相同配色。優先使用可辨識素材，SVG 可用於清楚的關係、圖表、遮罩與路徑。

## 安裝

```sh
git clone https://github.com/erduo1998-cell/erduo-broll-loop-engineering.git
cd erduo-broll-loop-engineering
./Install.command
```

安裝器準備固定版 HyperFrames、瀏覽器、FFmpeg 與 Skill 連結。安裝目錄須保留，完成後重新啟動 Codex 或 Claude Code。使用 v1.0.1 安裝包時，以該包的 README 為準。

```sh
node scripts/doctor.mjs
node scripts/uninstall.mjs
```

解除安裝預設保留使用者資料。

## 最短提示詞

```text
使用 erduo-broll-loop-engineering，把這份原始 SRT 和 design 做成 B-roll。
保留導演、章節製作與獨立審美的上下文隔離。
畫面效果優先，完成實際看片和必要返修，再交付完整預覽。
```

交付可編輯 HTML/CSS/JS、素材來源、依序排列的 H.264 鏡頭與完整預覽。預設正式輸出為無音軌 3840×2160、30fps；使用者指定規格優先，不自動加入全文字幕或音樂。

## 實測與限制

同輸入 32 秒對照中，獨立 Sol 的關鍵幀與接縫盲評偏好接力方案，使用者隨後選用 Y。兩組皆為1080p/30fps並通過真實解碼。只改 S02，8.569秒完成更新，其他三鏡保持逐位元組一致。

**尚未證明更省時間或 Token。** 新方案模型階段611.281秒，對照325.136秒，含環境故障與無效搜尋，不能當作乾淨的端到端速度比較。交接工具整理必要輸入，並不自動清除宿主注入的全部上下文，也不強制沙箱。[驗證記錄](docs/LEAN-WORKFLOW-VALIDATION.md)。

既有 Recipe/runtime-plan v1–v4、明確指定 Remotion/hybrid 時保持[舊流程](erduo-broll-loop-engineering/references/legacy-production.md)，不自動遷移。新流程長片、Windows、剪輯器 GUI 與跨後端視覺一致性尚未驗證。152張 Shotcraft 卡是可選參考，不是152個已驗證元件。

## 開發

```sh
npm test
npm run task:creative -- --project /path/to/project --role director
npm run render:lean -- --project /path/to/project --quality draft
```

[製作命令](erduo-broll-loop-engineering/references/lean-production.md) · [動效參考](erduo-broll-loop-engineering/references/motion-patterns.md) · [隱私](PRIVACY.md) · [支援範圍](SUPPORT-MATRIX.md) · [更新記錄](CHANGELOG.md) · [MIT](LICENSE)
