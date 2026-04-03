# 西北旺跑步大本营 - 网站说明

> 北京·西北旺·公益跑团 静态官网

## 文件结构

```
xbwrun-site/
├── index.html          # 主页面（包含全部 CSS 和渲染逻辑）
├── data/
│   ├── site.js         # 网站基础信息（名称、Logo、微信号、统计数据）
│   ├── events.js       # 大事记数据
│   └── activities.js   # 日常活动记录
└── README.md           # 本说明文件
```

---

## 如何更新内容

### 更新「大事记」

编辑 `data/events.js`，在 `EVENTS` 数组中添加或修改条目：

```js
const EVENTS = [
  {
    date: "2026-06",          // 年月，格式 YYYY-MM
    title: "夏季集训开营",     // 标题
    desc: "20人参与，完成首次高强度集训", // 描述
    tag: "活动"               // 标签：「活动」或「里程碑」
  },
  // ... 其他条目
]
```

**Tag 类型：**
- `"里程碑"` — 紫色标签，适合重要节点（成立、完赛等）
- `"活动"` — 蓝色标签，适合常规活动记录

> 条目顺序即展示顺序，建议最新的放在最前面。

---

### 更新「日常活动」

编辑 `data/activities.js`，在 `ACTIVITIES` 数组中添加或修改条目：

```js
const ACTIVITIES = [
  {
    date: "2026-04-08",       // 日期，格式 YYYY-MM-DD
    title: "周三速度训练",     // 活动标题
    desc: "间歇跑×8组，配速5:10，15人参与", // 活动描述
    emoji: "⚡"               // 表情图标
  },
  // ... 其他条目
]
```

> 建议保留最近 6-9 条记录，过多会导致页面过长。

---

### 更新基础信息

编辑 `data/site.js` 可修改：
- `name` — 网站名称
- `logoText` — 导航 Logo 文字（建议2字）
- `wechat` — 微信号
- `stats` — Hero 区统计数字（图标/数值/标签）

---

## 部署到 GitHub Pages

### 方法一：通过 GitHub 网页界面（推荐新手）

1. 登录 [GitHub](https://github.com)，点击右上角 **「+」→「New repository」**
2. 仓库名填写（例如）`xbwrun`，设置为 **Public**，点击 **Create repository**
3. 将 `xbwrun-site/` 目录下的所有文件上传到仓库根目录
4. 进入仓库 **Settings → Pages**
5. Source 选择 **Deploy from a branch**，Branch 选 `main`，目录选 `/ (root)`
6. 点击 **Save**，等待约 1-2 分钟
7. 访问 `https://你的用户名.github.io/xbwrun/` 即可

### 方法二：通过 Git 命令行

```bash
# 1. 在 xbwrun-site/ 目录下初始化 Git
cd xbwrun-site
git init
git add .
git commit -m "初始化西北旺跑步大本营网站"

# 2. 关联 GitHub 远程仓库（替换为你的仓库地址）
git remote add origin https://github.com/你的用户名/xbwrun.git
git branch -M main
git push -u origin main

# 3. 开启 GitHub Pages（在 GitHub 网页 Settings → Pages 中设置）
```

### 自定义域名（可选）

如果有自己的域名（如 `xbwrun.cn`），在仓库根目录创建 `CNAME` 文件，写入域名：

```
xbwrun.cn
```

然后在域名提供商处添加 CNAME 记录指向 `你的用户名.github.io`。

---

## 技术说明

- **纯静态**：HTML + CSS + 原生 JavaScript，无需任何构建工具或框架
- **数据驱动**：大事记和活动数据通过 `data/*.js` 外部文件管理，方便非技术人员更新
- **响应式**：完整支持手机/平板/桌面，768px 断点自适应
- **滚动动画**：使用 IntersectionObserver 实现元素入场动画
- **字体**：Outfit（英文/数字）+ Noto Sans SC（中文），通过 Google Fonts CDN 加载

---

## 联系

微信：**xbwrun**  
北京·西北旺·公益跑团

© 2026 西北旺跑步大本营
