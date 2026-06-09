# Prompt Rules

本文件定义图片生成提示词规则。

目标是让图像模型生成：

- 4 张独立图片
- 竖版 3:4
- 小红书旅行招募风
- 信息清楚
- 风格统一
- 不生成四宫格
- 不把 4 张拼成一张
- 尽量减少中文乱码和小字错误

---

# 1. Output Separation Rules

最终必须分别生成 4 张图片。

每张图片都必须作为独立画面生成。

生成时必须明确：

- Generate image 1 only
- Generate image 2 only
- Generate image 3 only
- Generate image 4 only

禁止在提示词中出现：

- four-panel layout
- collage of four posters
- 4-in-1
- grid layout
- four cards in one image
- combined poster
- long image containing all pages

中文禁止表达：

- 四宫格
- 拼图
- 合集图
- 四张合成一张
- 长图合集
- 组图排在同一画布

如果需要生成 4 张，应分别调用 4 次生成，而不是一次生成一张合集图。

---

# 2. Aspect Ratio Rules

每张图片必须是：

- vertical poster
- 3:4 aspect ratio
- 小红书竖版比例
- 单页海报

提示词中必须明确：

“vertical 3:4 single-page Xiaohongshu travel recruitment poster”

---

# 3. Text Reliability Rules

图像模型容易生成乱码、错字、小字糊掉。

因此图中文字必须少而大。

## 推荐文字策略

优先使用：

- 大标题
- 短标签
- 少量英文
- 编号
- 简短时间节点

避免使用：

- 长段中文
- 密集小字
- 多行复杂说明
- 复杂表格
- 过多时间节点
- 超过 8 个文字模块

## 中文标题规则

中文主标题必须：

- 字数短
- 4～8 个中文字优先
- 足够大
- 不要使用罕见字
- 不要多层描边
- 不要变形过度

## 英文规则

英文只作为装饰辅助，必须短。

例如：

- WEEKEND TRIP
- ROUTE FLOW
- HIGHLIGHTS
- BEFORE WE GO
- OUTDOOR JOURNEY

## 小字处理

如果需要较多说明文字，应使用：简短标签、编号结构、视觉占位块、可读性优先。

不要让模型生成密密麻麻的小字。

---

# 4. Prompt Structure

每张图片提示词必须按以下结构组织：

## 背景 / 场景

说明使用哪类图片作为视觉基础，以及背景处理方式。

## 主题

说明这是哪一页：首图、行程节奏图、亮点展示图、注意事项图。

## 关键细节

说明排版、文字层级、路径线、标签、图文关系等。

## 限制条件

说明禁止内容，如不要四宫格、不要拼图、不要电商感、不要密集小字等。

---

# 5. Shared Style Injection

无论使用哪种风格，每张提示词都必须注入当前选择的 Style Profile。

必须包含：

- 风格名称
- 色彩方向
- 字体气质
- 排版气质
- 装饰语言
- 禁止项

例如，使用电影感轻旅招募风时，应包含：

- real travel photography as main visual
- cinematic poster feeling
- low saturation natural color palette
- elegant Chinese serif title
- small uppercase serif English
- thin line decoration
- refined spacing
- no cheap travel agency ad style

---

# 6. Page-Specific Prompt Rules

## Image 01 Prompt Rules — 首图

必须明确：

- Generate image 1 only
- vertical 3:4
- single-page poster
- main cover image
- large Chinese title
- minimal text
- cinematic atmosphere
- travel recruitment cover
- no itinerary details

首图提示词应强调：大标题、氛围、目的地、核心玩法、少量标签、价格或详询客服。

禁止：完整时间轴、注意事项、装备清单、密集信息、四宫格拼图。

---

## Image 02 Prompt Rules — 行程节奏图

必须明确：

- Generate image 2 only
- vertical 3:4
- single-page poster
- C version route-flow itinerary design
- not a table
- not a normal list
- route-flow visual
- floating time nodes
- thin flowing path line
- time + scenic point + activity
- emphasize time progression

推荐提示词关键词：

- route-flow itinerary poster
- floating timeline nodes
- thin curved path line
- travel route annotation
- scenic background
- time progression
- visual movement
- clean readable labels

禁止：table、spreadsheet、dense itinerary text、normal vertical list、map app screenshot、four-panel collage、combined poster。

---

## Image 03 Prompt Rules — 亮点展示图

必须明确：

- Generate image 3 only
- vertical 3:4
- single-page poster
- highlights page
- 3 to 5 highlights
- short visual labels
- magazine layout
- experience-driven

可选择：

- multi-photo editorial sections
- single strong photo with floating highlight annotations

禁止：long paragraphs、too many stickers、dense guide text、itinerary timeline、warning notes。

---

## Image 04 Prompt Rules — 注意事项图

必须明确：

- Generate image 4 only
- vertical 3:4
- single-page poster
- before-you-go notes
- clean reminder page
- 4 to 6 concise reminders
- calm and trustworthy design

提示词应强调：清爽、有秩序、可信赖、极简图标、细线分割、文字少而清楚。

禁止：scary warning style、dense legal text、red alert design、crowded small text、contract-like layout、four-panel collage。

---

# 7. Negative Prompt Rules

每张图片都必须包含负面限制：

- no four-panel layout
- no grid layout
- no collage of four posters
- no combined poster
- no long infographic
- no cheap travel agency advertisement
- no ecommerce promotion style
- no dense small text
- no unreadable text
- no excessive stickers
- no cluttered layout
- no red-yellow loud color scheme
- no heavy outline fonts
- no cartoonish typography unless selected style requires hand-drawn elements
- no fake QR code
- no fake logo unless user provides logo
- no invented phone number
- no invented price
- no invented meeting point

---

# 8. Handling Missing Commercial Info

如果价格、集合点、成团人数等商业信息缺失，提示词中不要编造。

可以使用：

- 详询客服
- 联系客服咨询
- 以出行通知为准
- 小团出行
- 参考行程

不要生成：

- 假电话号码
- 假二维码
- 假价格
- 假集合地址
- 假公司资质

---

# 9. Typography Safety

为了降低文字错误风险：

## 中文

只放短文字。推荐主标题、页面标题、关键词标签、简短时间节点。避免大段中文说明、复杂地名堆叠、很长的路线名、难写罕见字。

## 英文

只放短英文装饰。不要生成长英文段落。

## 时间节点

第 2 张图的时间节点可以保留，但每个节点必须短。

推荐：

- 08:00 出发
- 10:30 入谷
- 12:00 午餐
- 14:00 玩水
- 16:30 返程

如果模型不擅长长中文，可以把节点设计为：08:00、10:30、12:00、14:00、16:30，并用较少中文标签辅助。

---

# 10. Final Generation Checklist

生成前检查：

- 是否选择了风格？
- 是否完成信息补全？
- 是否没有编造商业信息？
- 是否为 4 张独立图片？
- 是否每张都是 3:4？
- 是否没有四宫格？
- 第 2 张是否为路线流动式？
- 每张图是否只讲一个核心信息？
- 图中文字是否足够少？
- 整组风格是否统一？
