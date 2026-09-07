# Erduo B-roll Loop Engineering

**把原始 SRT 与设计要求，做成看得懂、能修改的 B-roll。**

[English](README.en.md) · [日本語](README.ja.md) · [한국어](README.ko.md) · [繁體中文](README.zh-TW.md)

> 当前工作树包含尚未发布的轻量流程。GitHub 最新正式版本仍为 [v1.0.1](https://github.com/erduo1998-cell/erduo-broll-loop-engineering/releases/tag/v1.0.1)。新流程的实测范围与限制见 [开发验证记录](docs/LEAN-WORKFLOW-VALIDATION.md)；不把旧版耗时当成新版成绩。

## 现在怎么做片

```text
原始 SRT ＋ design ＋ 可选素材
  → 创作负责人直接设计和制作
  → 一份镜头计划 ＋ 每镜可编辑源码
  → 快速预览、实际看片、局部修改
  → 按授权输出正式镜头与完整预览
```

普通任务直接由一个创作负责人完成。长片按连续章节分工，素材搜索量大时才增加素材人员。每次不再固定启动 Director、Assets、Lead 和多个 Builder，也不再固定做三类样片及五镜比赛。

新风格可以先试一个关键片段。已经明确的任务直接制作，尊重用户要求的暂停和审看点。版本升级的五镜盲测作为可选的旧流程保留。

最短提示词：

```text
使用 erduo-broll-loop-engineering，把这份 SRT 和 design 做成 B-roll。
采用轻量流程，优先使用可识别的素材和清楚的信息表达。
请完成制作、观看和修改，再给我预览。
```

## 画面与效率

- **具体的东西用具体画面。** 人物、产品、页面和场景优先用合适的照片、视频、截图或用户素材。素材不足时用清楚的文字和真实关系表达。
- **SVG 有合适用途。** 图标、数据图表、标注和遮罩可以使用；不再默认用手绘复杂 SVG、抽象线条或粒子代替主体。
- **一个计划即可。** SRT 时间、镜头目的、主体和素材路线写在 `broll-plan.json`；文件身份、渲染事实和索引交给脚本。
- **先快速看，再正式输出。** 预览与正式输出分开。修改后复用未变化的镜头，重建受到实际依赖影响的镜头和预览。
- **实际看片。** 创作负责人查看检查图和动态预览，修掉看不清、素材缺失、动作遮挡和表达含糊等问题。
- **如实计量。** 记录实际渲染、复用和耗时；Token 只使用宿主真实用量，文件字节不是 Token。

## 交付

每镜独立 H.264 MP4、按顺序排列的索引、完整预览，以及可以继续编辑的 HTML/CSS/JS 和素材来源。默认正式输出 3840×2160、30fps，用户指定画幅/帧率优先。默认静音，不重复烧字幕，不自动加音乐。

[精简制作契约与命令](erduo-broll-loop-engineering/references/lean-production.md) · [视觉选择指南](erduo-broll-loop-engineering/references/lean-visual-direction.md)

## 安装

首次安装可从仓库完整准备环境：

```sh
git clone https://github.com/erduo1998-cell/erduo-broll-loop-engineering.git
cd erduo-broll-loop-engineering
./Install.command
```

安装器准备项目固定的 HyperFrames 环境、浏览器、FFmpeg 和 Skill 链接。安装目录需要长期保留；安装完成后重启 Codex 或 Claude Code。下载已发布包时，以该版本 README 的流程为准。

```sh
node scripts/doctor.mjs
node scripts/uninstall.mjs
```

卸载默认保留用户数据。完整说明见 [隐私](PRIVACY.md)、[支持范围](SUPPORT-MATRIX.md) 和 [安装贡献说明](CONTRIBUTING.md)。

## 兼容旧项目

已有 Recipe/runtime-plan v1–v4 项目继续走 [v1.0.1 兼容流程](erduo-broll-loop-engineering/references/legacy-production.md)，保持其原有审批和输入。明确要求 Remotion/hybrid 时也走兼容路线；新轻量流程先支持 HyperFrames，不自动迁移或切换后端。

152 张 Shotcraft 卡仍可按实际技法问题查询；它们不是 152 个已经验证的 HyperFrames 动画组件。卡库不会自动进入每次任务的上下文。

## 历史实测与限制

[v1.0.0 实测](docs/V1.0.0-BENCHMARK.md)：179.866 秒输入，第一次完整预览约 242.05 分钟，宿主 Token 未知。v1.0.1 的五镜 canary 获用户认可，剩余长片由用户取消，不能视为完整长片验收。

[历史 40 秒展示](docs/images/demos/homepage-showcase.gif) 展示的是旧版能力，不是新轻量流程的性能证明。Windows、剪映/CapCut GUI、跨后端视觉一致性以及当前新版长片表现不作未验证承诺。

## 隐私与网络

仓库自身不采集或发送遥测，子进程默认设置 `HYPERFRAMES_NO_TELEMETRY=1`。首次安装可能访问 Node.js 官方目录、npm registry、GitHub 和 HyperFrames 浏览器源；使用素材搜索时才访问所选服务。SRT、源码、素材和渲染结果默认留在本机，凭证不进入项目或输出。本仓库只能约束自己启动的进程，单独调用外部 HyperFrames 时以其自身实现和政策为准。

## 开发

```sh
npm test
npm run plan:lean -- --project /path/to/project
npm run render:lean -- --project /path/to/project --quality draft --hyperframes /path/to/hyperframes
```

[更新记录](CHANGELOG.md) · [MIT License](LICENSE) · [第三方说明](THIRD-PARTY-NOTICES.md)

作者：刘冉 / 耳朵 · [GitHub](https://github.com/erduo1998-cell) · [主页](https://erduo.art)
