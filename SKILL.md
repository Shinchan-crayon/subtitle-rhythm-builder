---
name: subtitle-rhythm-builder
description: 根据 WhisperX 时间戳整理 Shin-video 字幕节奏，修正断句过碎、停留过短、字幕过长等问题，并把结果合并进 runtime/scenes.json。
---

# 字幕节奏整理

优化 `runtime/scenes.json` 里的字幕节奏。

## 目标

让字幕看起来像短视频字幕，而不是机械转写文本。

## 规则

- 每条字幕尽量是一句完整意思。
- 单条字幕不要过长。
- 字幕停留时间不要太短。
- 不要把语气词单独切成一条。
- 不要破坏 WhisperX 的整体时间顺序。

## 输出

直接更新或生成带字幕节奏的：

```text
runtime/scenes.json
```

## 注意

这个 Skill 不单独暴露给用户。它只是保证最终视频的观看体验。
