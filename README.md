# 西北旺跑步大本营 - 网站说明

> 北京·西北旺·公益跑团 静态官网

## 文件结构

```
xbwrc.github.io/
├── index.html              # 主页面（包含全部 CSS、渲染逻辑与静态内容）
├── data/
│   ├── site.js             # 网站基础信息（名称、Logo、微信号、Hero 统计数据）
│   ├── events.js           # 大事记数据（首页未渲染时作为保留数据）
│   └── activities.js       # 日常活动记录（首页未渲染时作为保留数据）
├── assets/
│   ├── qr/                 # 各类二维码图片（扫码卡片用）
│   │   ├── wechat-official.png   # 关于我们 · 微信公众号
│   │   ├── wechat-channel.png    # 关于我们 · 视频号
│   │   ├── douyin.png            # 关于我们 · 抖音
│   │   ├── xiaohongshu.png       # 关于我们 · 小红书
│   │   ├── video-download.png    # 训练资源 · 视频下载（http://v.xbw.run）
│   │   ├── wotu-album.png        # 训练资源 · 跑团相册（http://t.xbw.run）
│   │   ├── wechat-group.png      # 加入我们 · 微信群
│   │   └── miniprogram.png       # 加入我们 · 小程序
│   └── about/              # 关于我们相关静态图片资源
└── README.md
```

---

## 页面模块

| 区块 | 锚点 | 说明 |
| --- | --- | --- |
| Hero | `#hero` | 跑团定位、Hero 统计数据（由 `data/site.js` 驱动） |
| 关于我们 | `#about` | 简介 / 活动介绍 / 大事件 / 组织架构（info-card 图文）+ 关注我们二维码 |
| 最新消息 | `#news` | 新闻卡片（当前为硬编码，跳转微信图文） |
| 资源链接 | `#resources` | 视频下载、跑团相册（二维码卡，可点击跳转外链） |
| 加入我们 | `#join` | 微信群二维码 + 小程序（图片 + 可复制跳转链接） |
| Footer | — | 品牌介绍、快捷入口 |

---

## 如何更新内容

### 更新 Hero 统计数据 / 站点基础信息

编辑 `data/site.js`：

- `name` — 网站名称
- `logoText` — 导航 Logo 文字（建议 2 字）
- `wechat` — 微信号（未在当前页面 DOM 使用，保留字段）
- `stats` — Hero 区统计卡片（图标 / 数值 / 标签），4 项

### 更新「活动介绍」（品牌活动 / 常规活动）

直接编辑 `index.html` 中 `.info-card-body` 内 "活动介绍" 卡片下的两组列表：

- `品牌活动` 下的 `.info-card-list-item`
- `常规活动` 下的 `.info-card-list-item`

分组标题由 `.info-card-list-group` 控制，紫色小号加粗样式。

### 更新「最新消息」

编辑 `index.html` 中 `#news` section 内的 `.news-card`：

- `data-status`/`is-ended` 类控制活动是否已结束（灰化标签与标题）
- `href` 指向对应图文链接

### 更新二维码 / 资源外链

- 替换 `assets/qr/` 下同名 PNG 即可（推荐 720×720，圆点渐变风格）
- 外链地址（视频下载 / 跑团相册）在 `index.html` 中 `#resources` 区块的 `a.qr-card-link` 的 `href` 上修改
- 小程序跳转链接在 `.copy-chip[data-copy]` 属性中修改

### 更新大事记 / 日常活动（如需重新启用）

当前首页未动态渲染 `EVENTS` 与 `ACTIVITIES`，但数据保留在 `data/events.js` / `data/activities.js` 中。如需启用，在 `index.html` 脚本中增加 `#timeline`、`#activitiesGrid` 等挂载点即可；字段格式：

```js
// events.js
{ date: "2025-10", title: "…", desc: "…", tag: "里程碑" | "活动" }

// activities.js
{ date: "2026-04-08", title: "…", desc: "…", emoji: "⚡" }
```

---

## 响应式适配

CSS 内已针对 `1024 / 768 / 480 / 360` 四档屏宽做适配：

- 容器内边距、section 间距、卡片内边距随屏宽递减
- Hero 双栏 → 单栏；多列卡片 → 两列/单列
- Timeline 左侧缩进与圆点尺寸缩小
- 小程序复制胶囊在 ≤480 变为上下两行全宽布局

---

## 部署

纯静态页面，直接托管于 GitHub Pages（仓库名 `xbwrc.github.io`）。推送到 `main` 分支即自动发布。

---

## 联系

微信：**xbwrun**  
北京·西北旺·公益跑团

© 2026 西北旺跑步大本营
