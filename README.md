<h1 align="center">Crayon-xin</h1>

<p align="center">
  <strong>把喜欢的画面，变成一幅蜡笔画。</strong><br>
  三种画法 · 按部件配色 · 保留原画
</p>

<p align="center">
  <a href="https://github.com/smallmb/Crayon-xin/archive/refs/heads/main.zip"><img src="https://img.shields.io/badge/下载-Skill-2563eb?style=for-the-badge" alt="下载 Skill"></a>
  <a href="https://github.com/smallmb/Crayon-xin"><img src="https://img.shields.io/badge/适用-Codex-111827?style=for-the-badge" alt="适用于 Codex"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-10b981?style=for-the-badge" alt="MIT License"></a>
</p>

<p align="center">
  <a href="#快速开始">使用指南</a> ·
  <a href="https://github.com/smallmb/Crayon-xin/commits/main/">更新记录</a> ·
  <a href="https://github.com/smallmb/Crayon-xin/issues/new">反馈问题</a>
</p>

一张图片即可开始，无需额外风格参考。支持人像、风景、建筑、动物与静物，让线稿有颜色，让照片有手绘质感。

## 一张原图，三种画法

从细腻叠色到绵密色料，再到奔放笔触。点击图片查看大图。

<table>
  <thead>
    <tr><th width="25%">原图</th><th width="25%">细腻蜡笔 · 默认</th><th width="25%">绵密油画棒</th><th width="25%">粗犷蜡笔</th></tr>
  </thead>
  <tbody>
    <tr>
      <td><a href="references/examples/portrait-01-source.jpg"><img src="references/examples/portrait-01-source.jpg" width="240" alt="长发人物：原图"></a></td>
      <td><a href="references/examples/portrait-01-crayon.png"><img src="references/examples/portrait-01-crayon.png" width="240" alt="长发人物：细腻蜡笔"></a></td>
      <td><a href="references/examples/portrait-01-oil-pastel.png"><img src="references/examples/portrait-01-oil-pastel.png" width="240" alt="长发人物：绵密油画棒"></a></td>
      <td><a href="references/examples/portrait-01-expressive.png"><img src="references/examples/portrait-01-expressive.png" width="240" alt="长发人物：粗犷蜡笔"></a></td>
    </tr>
    <tr>
      <td><a href="references/examples/portrait-02-source.jpg"><img src="references/examples/portrait-02-source.jpg" width="240" alt="侧脸人物：原图"></a></td>
      <td><a href="references/examples/portrait-02-crayon.png"><img src="references/examples/portrait-02-crayon.png" width="240" alt="侧脸人物：细腻蜡笔"></a></td>
      <td><a href="references/examples/portrait-02-oil-pastel.png"><img src="references/examples/portrait-02-oil-pastel.png" width="240" alt="侧脸人物：绵密油画棒"></a></td>
      <td><a href="references/examples/portrait-02-expressive.png"><img src="references/examples/portrait-02-expressive.png" width="240" alt="侧脸人物：粗犷蜡笔"></a></td>
    </tr>
  </tbody>
</table>

## 画面里的细节，也有各自的颜色

- **分区上色**：头发、肤色、眼睛、衣料与小配件分别处理，腮红也有轻重过渡。
- **三种画法**：默认细腻蜡笔，可选绵密油画棒或粗犷蜡笔；笔触强度与结构简化分别调整。
- **保留原画**：以原构图和背景为依据，保留关键轮廓，生成后读取结果自检。

彩色图默认保色；黑白线稿可进行艺术补色，也可指定保持黑白。上方配色为创作示例，不是固定色板。

## 快速开始

1. **下载**本仓库，让支持参考图编辑的 Agent 读取 [SKILL.md](SKILL.md)。
2. **上传**你想转换的图片。
3. **发送**这句话：

> 把这张图转成蜡笔风，保留构图和背景，按不同部件配色，生成后先自检再展示。

想换种表现？加上「绵密油画棒」「粗犷蜡笔」「保持黑白」，或附一张喜欢的效果图。还可指定「笔触轻／中／强」与「结构简化低／中／高」。

<details>
<summary>作为 Codex Skill 使用</summary>

将仓库文件放入 `~/.codex/skills/universal-crayon-style-transfer/`，保持目录结构。在新会话中附图，并使用 `$universal-crayon-style-transfer` 调用。

</details>

---

[技能规则](SKILL.md) · [风格指南](references/style-guide.md) · [原图与效果图](references/examples/) · [MIT License](LICENSE)

<sub>示例为人像实测；其他题材仍需更多验证。需要宿主提供图像编辑能力，实际效果受源图和模型影响。</sub>
