---
name: universal-crayon-style-transfer
description: Convert supplied portraits, landscapes, architecture, animals, plants, objects, sketches, comics, or photos into crayon or oil pastel illustrations. Support source color preservation, sketch colorization, optional style references, and visual review. 图片转蜡笔画或油画棒，按部件配色并保留构图与环境。
---

# Universal Crayon Style Transfer

将源图转换为蜡笔或油画棒插画。默认延续细腻轻彩、分区配色、保留原画结构的效果。

## 1. 解析输入

先读取源图；用户指定的效果参考也须读取。每张待转换图片是独立内容源，参考图只决定获准的画法与色彩关系。多张源图逐张生成，不跨图借用主体。没有可读取的源图时请用户附图。

为本次编辑形成简短计划，无需把完整计划展示给用户：

- **结构**：题材、主体数量、姿势、比例、取景、宽高比、遮挡、透视、关键身份或物种特征、原有道具及明暗分组。
- **环境**：简单底色或复杂场景；主要区域的位置、颜色、远近、光源与投影。白底保持中性白，黑底保持近黑；透明底按工具能力保留。全画幅环境是画面内容。
- **色彩模式**：彩色源图默认保色；明确要求黑白则所有区域严格灰度；未上色线稿默认允许克制的艺术补色；指定参考时迁移对应色彩关系。补色属于创作选择，不声称恢复未知真实颜色。
- **分区配色**：列出实际可辨的部件及其底色、阴影色、必要的细节色。人物含发、肤、眼、衣料、衣领与配件；其他题材按天空/地面、毛色/鼻爪、器物/把手等拆分。保色时以原图为准，补色时允许协调的新颜色。

结构和环境以源图为依据；用户明确要求的改变优先。保留原有遮挡，不补造不可见部件。用户只说“转蜡笔风”时直接使用默认设置。

## 2. 选择媒介与表现强度

三种预设是起点，笔触强度与结构简化可以独立调整。用户参考优先于预设；参考图不会自动改变源图内容。

| 预设 | 触发与正向锚点 |
| --- | --- |
| A · 细腻轻彩蜡笔（默认） | `softly layered wax crayon, fine paper tooth, delicate broken contours, translucent light strokes, densely layered dark pigment` |
| B · 绵密油画棒 | “油画棒、油润、绵密”时选用：`creamy oil pastel, rich velvety pigment, softly blended color transitions, tactile pigment on textured paper`；用户要求厚涂时再加入 `subtle impasto ridges` |
| C · 粗犷蜡笔表现 | “粗犷、重肌理、奔放”时选用：`bold expressive crayon strokes, visible paper tooth, energetic form-following hatching, broad layered color blocks` |

- **笔触强度**：轻／中／强，默认 A 轻至中、B 中、C 强。控制颗粒、线宽、露纸和色料厚度；饱和度另按源图或用户要求决定。油画棒可以低饱和，粗犷也可以保持精确轮廓。
- **结构简化**：低／中／高。漫画与线稿默认低，保留眼形、表情和发束关系；照片默认中，概括微细纹理但保留身份、姿势与核心形状；“绘本、稚拙、童趣”可选高。高简化也要保留关键剪影、数量、透视、遮挡与辨识特征，不自动改成幼儿比例。

生成前读取 [风格指南](references/style-guide.md) 的“材质与配色”，再读本次涉及的题材模块。混合场景组合适用；不把人像处理套给其他主体。

## 3. 组装提示词并生成

使用当前宿主实际提供的参考图编辑工具，传入原始源图。工具支持时同时传入用户指定参考，并标明图片角色；只支持一图时传源图，将参考画法写成文字。保留原宽高比或选择最接近的可用尺寸。遵守宿主工具规范，不假定特定平台连接器存在。

按以下四段式英文模板填写，只留下适用内容，不将占位符直接发给工具：

```text
MEDIUM: Render the supplied source as [selected medium anchors]. Use [stroke intensity] texture and [structural abstraction] simplification. [Relevant style-reference characteristics, if supplied.]

STRUCTURE: Preserve the source composition, framing, aspect ratio, subject count, pose, proportions, camera angle, perspective, and occlusion. Retain [observed identity cues, silhouettes, and essential existing details]. Simplify [secondary details appropriate to the selected abstraction].

COLOR AND SUBJECT: Use [source-color preservation / strict grayscale / artistic colorization / authorized reference palette]. Map each visible region separately: [region: base color, shadow color, material treatment; repeat as needed]. [Relevant subject-specific rendering instructions.]

ENVIRONMENT AND LIGHT: Keep [observed background regions, positions, colors, and depth]. Preserve [light direction, value grouping, and important shadows]. Apply [selected medium treatment] consistently while retaining the environment's original tonal character.
```

逻辑约束先在内部检查，提示词优先写目标状态。例如白底写 `neutral white background with subtle white paper tooth`，遮眼发型写 `the fringe continues to cover the same eye`，漫画眼睛写原有眼形和表情。不要把历史失败清单整段粘进提示词；仅对本次确有风险的结构加简短限制。正向表达不保证模型一定遵守，最终仍以视觉检查为准。

## 4. 读取结果并分级自检

展示前必须实际读取生成图，与源图、选定配置及有效参考对照。工具成功不代表检查通过；无法读取时明确说明未完成视觉检查。只检查实际存在的题材与部件。

| 等级 | 判定 | 处理 |
| --- | --- | --- |
| P0 · 内容或请求违背 | 主体增减，明显换脸/换物种，姿势或核心轮廓改变，关键内容被裁切，背景被替换，环境结构严重丢失，严格黑白出现彩色 | 优先修正；修正后仍有 P0，停止并说明具体问题，不作为忠实转换的最终交付 |
| P1 · 核心风格偏差 | 选定媒介不明显，整图统一染色造成材质混同，主要部件漏涂，漫画五官被明显幼化，主体明暗或环境色调显著偏移 | 如有修正机会则处理；仍有偏差但无 P0 时，展示最符合请求的可用版本，简短说明实际偏差，不宣称完全通过 |
| P2 · 局部细节瑕疵 | 微小配件轻微色差，局部纸齿偏弱，细小边线差异，且不影响辨识或用户明确重点 | 直接交付；可感知且有用时附一句说明，不为细小问题消耗重绘机会 |

等级随用户重点调整：用户明确要求准确的标识、配件色或背景纯色，不能一律当作 P2。白纸的细微明度起伏也不等于背景替换。

每张源图本轮最多初次生成加一次视觉修正。存在 P0 时先解决 P0，仅合并与其相关且不冲突的 P1；没有 P0 时修正最主要的 P1，不堆入所有细节建议。修正提示词明确“观察到的偏差→目标状态→应保持的结构与画法”。以原始源图为内容依据，工具允许时将当前结果作为标明角色的风格辅助，避免只反复编辑衍生图而累积结构漂移。

修正后再次读取，优先选择无 P0 且最符合用户要求的版本。多图按源图顺序交付，单张失败不阻止其他可用结果。最终简短说明完成情况与实质偏差，并提供可用文件。

## 5. 失败边界

工具报错、拒绝或没有可用图片时，不换工具或改词反复硬试；修正调用失败也停止。已有可读取且无 P0 的结果可以按上述分级交付。无可用结果或持续 P0 时，说明实际问题，供用户选择获取风格指南，或另创同题材画面；用户选择后再生成。原创作品须明确区分于源图转换，不自动替代。
