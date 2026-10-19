# GSAP 动效图鉴

<p>
  <img src="https://img.shields.io/badge/GSAP-3.13-58e6a8?style=flat-square&logo=greensock&logoColor=0d1117" alt="GSAP 3.13">
  <img src="https://img.shields.io/badge/Demo-74-3b82f6?style=flat-square&logo=html5&logoColor=white" alt="74 个 Demo">
  <img src="https://img.shields.io/badge/依赖-0-f0883e?style=flat-square&logo=javascript&logoColor=white" alt="零依赖">
  <img src="https://img.shields.io/github/last-commit/LeoLee0812/gsap-gallery?style=flat-square&logo=github&label=最近更新" alt="最近更新">
  <img src="https://img.shields.io/github/commit-activity/w/LeoLee0812/gsap-gallery?style=flat-square&logo=github&label=本周提交" alt="本周提交">
  <img src="https://img.shields.io/github/repo-size/LeoLee0812/gsap-gallery?style=flat-square&logo=github&label=体积" alt="仓库体积">
  <img src="https://img.shields.io/badge/License-MIT-6e7681?style=flat-square" alt="MIT">
</p>

**74 个可交互的 GSAP 动效 demo**，按 GreenSock 官方 [gsap-skills](https://github.com/greensock/gsap-skills) 技能库全量覆盖。
每个 demo 都是一个独立的 HTML 文件，能直接玩、直接抄，全部离线运行，代码带中文注释。

**每天新增一个**：从 2026-10-18 起每天上线一个新动效，接下来要做的在 [ROADMAP.md](./ROADMAP.md)。

> 在线预览：<https://gsap.leolee0812.site>（Cloudflare Workers 托管）

---

## 这个项目解决什么问题

学 GSAP 时最大的障碍不是 API 难，而是**不知道有哪些动效可做、什么场景该用哪个**。
官方文档按 API 组织，你得先知道 `ScrollTrigger.batch` 存在，才能去查它。

这个仓库反过来，**按「你想做什么效果」组织**：想做滚动吸附？打开 `scrolltrigger-snap.html`，
里面三种模式实时切换、代码注释解释为什么这么写、底下列出坑在哪。

## 目录结构

```
gsap-gallery/
├── public/             # 站点根目录（Cloudflare Workers Static Assets）
│   ├── index.html      # 索引页（带搜索 + 分类筛选，本身也是个 demo）
│   ├── 404.html
│   ├── _headers        # lib/ 走一年强缓存
│   ├── demos/          # 74 个独立 demo，每个都是自包含的单文件
│   │   ├── ease-visualizer.html
│   │   ├── scrolltrigger-pin.html
│   │   └── ...
│   └── lib/            # GSAP 3.13 + 全部 25 个插件（本地副本，断网可用）
├── wrangler.jsonc      # Workers 配置
└── README.md
```

**每个 demo 都是自包含的单文件**——样式、结构、脚本全在一个 HTML 里。
想用哪个效果，把文件下下来改改就行，不用理解整个项目结构。

## 九个分类

| 分类 | 数量 | 讲什么 |
|---|---|---|
| **核心与手感** | 8 | 缓动曲线、错开节奏、变换属性、关键帧、循环、冲突处理、响应式降级 |
| **时间轴编排** | 3 | 位置参数、播放控制、嵌套时间轴 |
| **滚动叙事** | 14 | 触发时机、擦洗、钉住、吸附、批量入场、平滑锚点、视差 |
| **交互手感** | 14 | 拖拽惯性、统一手势、Flip 布局过渡、磁吸、3D 倾斜 |
| **文字动效** | 6 | 逐字、逐行、解码、打字机 |
| **UI 组件** | 12 | 弹窗、手风琴、标签页、Toast、进度环、跑马灯 |
| **SVG · 路径 · 物理** | 11 | 描线、形变、路径飞行、抛射、自定义缓动曲线 |
| **工具与性能** | 4 | gsap.utils 全套、quickTo、卡顿根因实测、调试面板 |
| **框架集成** | 2 | React/Next.js 的 useGSAP、Vue/Nuxt/Svelte 的生命周期与 SSR |

## 几个值得单独提的 demo

- **`ease-visualizer.html`** —— 38 条内置缓动曲线并排，曲线图和小球同步跑。
  「我的动画为什么很土」十次里有八次答案在这一页。
- **`transform-vs-layout.html`** —— 左右双屏实测 `x/y` 和 `left/top` 的性能差异，带 FPS 曲线和属性速查表。
- **`utils-playground.html`** —— `clamp` / `mapRange` / `snap` / `wrap` / `pipe` 等十个工具全部做成可拖拽的交互演示。
- **`scrolltrigger-pin.html`** —— pin 的完整用法，含 `pinSpacing` 左右对比和四个最难排查的坑
  （尤其是「祖先元素有 transform 会让 pin 彻底失效」这条）。
- **`quickto-performance.html`** —— 400 个点的压力测试，对比 `quickTo` 和每帧新建 tween 的差别。

## 本地运行

不需要构建，不需要 npm install：

```bash
git clone https://github.com/LeoLee0812/gsap-gallery.git
cd gsap-gallery

# 任选一种方式起个静态服务器
python3 -m http.server 8080 -d public
# 或
npx serve public
```

然后打开 <http://localhost:8080>。

> 直接双击 `public/index.html` 用 `file://` 打开也能跑，只是个别用到 `fetch` 的 demo 会受同源策略限制。

## 关于 GSAP 免费这件事

被 Webflow 收购后，**GSAP 全部插件已经免费商用**，包括以前 Club GSAP 会员专属的
SplitText、MorphSVG、DrawSVG、InertiaPlugin、CustomEase、GSDevTools 等。

```bash
npm install gsap    # 就这一行，全部插件都在里面
```

**不需要 `.npmrc`、不需要 auth token、不需要私有 registry。**
网上那些教你配私有源的教程都是收购前的，可以忽略。

## 技术选择说明

- **纯静态、零构建** —— 动效 demo 的价值在于「能直接复制走」，套上框架反而增加了理解成本。
- **库文件本地化** —— 不走 CDN，断网、地铁上、飞机上都能看。代价是仓库多了 460KB。
- **每个 demo 独立** —— 不抽公共样式、不抽工具函数。有重复代码，但换来的是任何一个文件都能单独拿走用。

## License

MIT。GSAP 本身遵循 [GreenSock 标准许可](https://gsap.com/standard-license)（现已免费商用）。
