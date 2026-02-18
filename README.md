# COCO Downloader (COCO音乐下载站)

![Next.js](https://img.shields.io/badge/Next.js-16.1-black)
![TypeScript](https://img.shields.io/badge/TypeScript-5.0-blue)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-4.0-38B2AC)
![License](https://img.shields.io/badge/License-MIT-green)

## 📖 简介

**COCO音乐下载站** 是一个基于 Next.js 16 构建的现代化音乐搜索与下载平台。界面设计简约纯净，支持多渠道音乐搜索、在线试听、批量下载，并配备了丝滑的暗黑模式（涟漪过渡动画）。

本项目致力于提供无广告、极速、纯净的音乐获取体验。

展示网站：[https://coco.cqapp.eu.org](https://coco.cqapp.eu.org)  (Vercel)

展示网站：[https://coco.wmfree.eu.org](https://coco.wmfree.eu.org)  (Netlify)

展示网站：[https://coco.wmapp.dpdns.org](https://coco.wmapp.dpdns.org)  (Netlify)
## ✨ 主要特性

- 🎵 **多源聚合搜索**：支持全网聚合搜索，内置多种音乐源渠道，一键切换。
- 🎧 **在线试听**：内置精美悬浮播放器，支持播放/暂停、进度拖拽、音量调节、上下曲切换。
- 🖱️ **便捷交互**：支持列表**双击播放**，鼠标悬停/选中效果优化，操作流畅。
- ⬇️ **批量下载**：支持多选歌曲，一键批量打包下载选中的音乐。
- 🌓 **极致主题体验**：
    - 完美适配**深色/浅色模式**。
    - 独家定制的**涟漪扩散**切换动画（基于 View Transitions API），视觉效果惊艳。
- ⚡ **现代化技术栈**：基于 React 19、Next.js 16 App Router、Tailwind CSS v4 构建。

## 🛠 技术栈

- **核心框架**: [Next.js 16.1.2](https://nextjs.org/) (App Router)
- **编程语言**: [TypeScript](https://www.typescriptlang.org/)
- **样式方案**: [Tailwind CSS v4](https://tailwindcss.com/)
- **动画库**: [Framer Motion](https://www.framer.com/motion/)
- **图标库**: [Lucide React](https://lucide.dev/)
- **主题管理**: [next-themes](https://github.com/pacocoursey/next-themes) + View Transitions API
- **后端处理**: Next.js API Routes + Axios + Cheerio

## 🚀 快速开始

### 环境要求

- Node.js >= 18.17.0
- npm / pnpm / yarn

### 1. 克隆项目

```bash
git clone https://github.com/markcxx/coco-downloader.git
cd coco-downloader
```

### 2. 安装依赖

```bash
npm install
# 或者
yarn install
# 或者
pnpm install
```

### 3. 运行开发服务器

```bash
npm run dev
```

打开浏览器访问 [http://localhost:3000](http://localhost:3000) 即可开始使用。

### 4. 构建生产版本

```bash
npm run build
npm start
```

## 📂 项目结构

```
coco-downloader/
├── src/
│   ├── app/                 # Next.js App Router 核心目录
│   │   ├── api/             # 后端 API 路由 (search, url, download)
│   │   ├── globals.css      # 全局样式 (含 Tailwind v4 配置)
│   │   ├── layout.tsx       # 根布局 (集成 ThemeProvider)
│   │   └── page.tsx         # 首页主要逻辑 (搜索、列表、交互)
│   ├── components/          # UI 组件
│   │   ├── Navbar.tsx       # 顶部导航栏 (含涟漪主题切换逻辑)
│   │   ├── PlayerBar.tsx    # 底部悬浮播放器
│   │   └── ThemeProvider.tsx# 主题上下文提供者
│   ├── lib/                 # 工具库
│   │   └── providers/       # 音乐源策略模式实现 (impl/gequbao.ts, impl/qqmp3.ts)
│   └── types/               # TypeScript 类型定义
├── public/                  # 静态资源文件
└── ...
```

## 🎨 特色功能实现解析

### 涟漪主题切换
在 `src/components/Navbar.tsx` 中，我们利用了浏览器原生的 `document.startViewTransition` API 配合 CSS `clip-path` 属性。
当用户点击主题切换按钮时，计算点击坐标，以该坐标为圆心，计算覆盖全屏所需的最大半径，然后执行圆形扩散遮罩动画。这比传统的 CSS `transition` 全局淡入淡出更具动感和现代感。

### 音乐源扩展
项目后端采用策略模式设计。在 `src/lib/providers` 下定义了统一的接口。若需添加新的音乐网站源，只需新建一个实现类并在工厂方法中注册即可，无需大幅修改前端逻辑。

## 🚀 部署方案

### 方案一：本地部署

```bash
npm run build
npm start
```

### 方案二：Docker 部署

```bash
docker build -t coco-downloader -f Dockerfile .
docker run -p 3000:3000 coco-downloader
```


## 🤝 贡献与反馈

如果您发现任何问题或有新功能建议，欢迎提交 Issue 或 Pull Request。

仓库地址：[https://github.com/markcxx/coco-downloader](https://github.com/markcxx/coco-downloader)

## 📄 许可证

MIT License
