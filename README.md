# 字幕节奏整理

> Shin-video AI 员工体系中的「字幕体验设计」Skill。它不是孤立提示词，而是整条文章转口播视频流水线的一环。

## 它能解决什么问题

ASR 原始切分容易出现一句话断一半、字幕停留太短、词语单独成条等问题。这个 Skill 让字幕按完整意思呈现，但不破坏整体时间顺序。

## 它在工作流里的位置

**阶段：** 第 6 步：字幕节奏修正

**上游：**
- scene-generator
- whisperx-transcriber

**下游：**
- remotion-video-director
- remotion-renderer

## 输入什么

- runtime/asr.json
- runtime/scenes.json
- 口播文案.md

## 输出什么

- 更新后的 runtime/scenes.json 或字幕节奏字段

## 背后由哪些能力组成

这个 Skill 自身负责：

- 避免字幕读不完就切走
- 避免字幕和主画面互相抢空间
- 让字幕跟随音频而不是被画面卡死

它通常由 `shin-video-director` 总控调用，也可以在当前项目材料已经准备好时单独调用。

## 每个 Skill 的作用

在完整 AI 员工体系里，本 Skill 的职责是：**字幕体验设计**。

它不负责：

- 不改写口播事实
- 不生成镜头语言
- 不替代导演层

## 演示截图 / 视频

![Shin-video Demo](docs/demo/style-comparison.png)

演示重点：演示截图展示机械断句和优化断句的对比。

完整视频 Demo 建议放在总控仓库或 ThinkAI Skill 页面中展示；单个 Skill 仓库保留截图和阶段说明，避免每个子仓库重复放大视频文件。

## 适合谁买

在意字幕观看体验的短视频制作者。

## 下载 / 安装方式

```bash
npx skills add https://github.com/Shinchan-crayon/subtitle-rhythm-builder
```

安装后，在支持 Skill 的 Agent 中说：

```text
请使用 字幕节奏整理，继续处理当前 Shin-video 项目。
```

## 付费版本和定制服务入口

- 免费版：安装本 Skill，按本地 Shin-video 工作流手动配置运行。
- 付费版：可提供整套工作流安装包、环境部署协助、示例项目和远程排障。
- 定制服务：可按行业定制口播风格、导演规则、Remotion 模板、品牌视觉系统和 ThinkAI 上架页面。

咨询入口：ThinkAI Skill 广场 / GitHub Issues / 私信定制咨询

## 验收标准

使用本 Skill 后，至少要能确认：

- 已正确生成或推进到：更新后的 runtime/scenes.json 或字幕节奏字段
- 没有绕过它的上游依赖。
- 没有把本 Skill 明确不负责的事情混进来。
- 出错时能说清楚卡在哪个输入或环境条件上。

## 能力边界

- 不改写口播事实
- 不生成镜头语言
- 不替代导演层

Shin-video 追求的是「可维护的本地视频生成工作流」，不是把所有能力塞进一个万能提示词。这个 Skill 只负责自己这一段，完整成片需要配合其它 AI 员工和本地 Shin-video 项目。
