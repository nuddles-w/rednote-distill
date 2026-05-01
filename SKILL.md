---
name: rednote-distill
description: >
  Distill any Xiaohongshu (RED/小红书) blogger from a profile link.
  Takes a RED profile URL, extracts available content, and outputs a structured
  report distilling: content style, viral mechanics, persona construction,
  copywriting patterns, and monetization strategy. Use when someone shares a RED
  blogger link and wants to "distill what makes this blogger work" or "learn the
  essence of their style". Also supports comparing two bloggers side by side.
---

# 蒸馏小红书博主 (RED Blogger Distiller)

给定一个小红书博主链接，蒸馏其内容策略和走红原因的精华，输出结构化分析报告。

## Quick Start

```
蒸馏这个博主：https://xhslink.com/xxx
```

## 蒸馏思路

不是简单搬运内容，而是把博主的成功经验「蒸馏」出来——剔除噪音，保留可复用的策略框架。

## 内容获取策略

小红书是 JS 渲染的。按优先级自动尝试提取：

### 方式 1: web_fetch（快，信息有限）
对 profile URL 使用 `web_fetch`，抓取静态 HTML 中的 Bio、粉丝数、名字。

### 方式 2: 浏览器自动化（更深）
`web_fetch` 只抓到 footer 时，切换到浏览器工具打开 profile 页面，截取可见笔记。

- 如果用户浏览器已有小红书登录态，使用 `profile="user"`。
- 遇到登录墙，停下来告诉用户：「小红书需要登录才能看内容，请先在浏览器里登录小红书，然后告诉我继续。」

### 方式 3: 手动粘贴（最可靠）
自动化都碰壁时，请用户复制 3-5 条代表性笔记：
```
我没法自动抓取她的笔记内容。你能把她最近 3-5 条爆款笔记的标题+正文复制过来吗？我来蒸馏。
```

## 蒸馏报告结构

对每个博主，输出以下章节：

### 1. 概览
- 身份、赛道、粉丝量级
- 一句话定位：「身份 + 差异化标签」
- 核心公式：驱动其成功的 1-2 个关键机制

### 2. 内容风格蒸馏

#### 命名
- 结构（双语？谐音梗？赛道关键词？）
- 为什么能成为记忆点

#### Bio
- 逐层蒸馏：身份锚 → 信任背书 → 破圈钩子 → 变现入口
- 每一层在向谁发信号

#### 内容栏目
识别 3-4 个重复出现的内容类型。每个：
- 名称和格式
- 在漏斗中的角色（信任 / 流量 / 转化 / 留存）
- 一个代表性例子

#### 文案模式
拿到帖子正文时可蒸馏：
- **标题钩子**：数字运用、好奇心缺口、情绪触发词、emoji 密度
- **开头**：身份代入、痛点直击、故事感、反常识
- **正文节奏**：段落长度、emoji 作为视觉断点、列表 vs 叙事
- **语言人设**：口头禅、语气（姐妹/宝子/兄弟）、自称方式
- **CTA 风格**：评论区引战、收藏提示、关注引导、软着陆

#### 视觉风格（有图片时）
- 配色倾向
- 封面文字布局
- 出镜策略
- 照片风格（冷暖、对比、生活化 vs 棚拍）

### 3. 为什么火（走红机制蒸馏）

- **身份钩子**：在赛道里凭什么脱颖而出
- **情绪引擎**：内容触发什么情绪（向往、好奇、FOMO、释然、愤怒）
- **共鸣机制**：如何拉近与读者的距离
- **平台契合度**：如何利用小红书的算法/用户行为
- **内容护城河**：什么别人抄不走

### 4. 可蒸馏的关键要点

3-5 条可操作的学习点：
- 哪些能学（可复制的模式）
- 哪些不能抄（学过来反而假）
- 怎么结合自己的背景

### 5. 横向对比（蒸馏两个博主时）

| 维度 | 博主 A | 博主 B | 关键差异 |
|---|---|---|---|
| 定位 | | | |
| 赛道切入 | | | |
| 走红机制 | | | |
| 变现路径 | | | |
| 受众画像 | | | |

## 使用注意

- **始终透明**：明确告知用户自动提取到了什么、没提到什么
- Bio 本身就是浓缩的策略——一份好的小红书 Bio 里藏着完整定位，优先蒸馏
- 用户想模仿时，在蒸馏报告后询问是否需要生成个性化方案，参见 [references/IMITATION.md](references/IMITATION.md)
- 其他平台（抖音、YouTube、Twitter）同样适用此蒸馏框架
