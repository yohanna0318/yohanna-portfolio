[README.md](https://github.com/user-attachments/files/34789310/README.md)
# Yara 陈燕红 · 个人作品集

这是一个以品牌与 IP 设计为核心的交互式个人作品集网站。通过滚动视频、角色舞台和项目案例，展示从视觉创意到实体包装、活动传播与品牌应用的设计过程。

网站面向招聘方、设计负责人和潜在合作客户，目标是让访客快速了解 Yara 的设计能力、项目经验与合作方向。

> 当前版本包含完整前台、可直接部署的静态文件及组件源码。内容管理后台尚未开发。

## 项目预览

![包装设计项目详情预览](.10k/pack-desktop.jpg)

<details>
<summary>查看手机首页</summary>

<img src=".10k/mobile-project-entry-v3.jpg" alt="手机首页与看精选作品入口" width="280">

</details>

## 可以体验什么

- **滚动驱动的动态首页**：人物视频随页面滚动推进，手机首屏提供“看精选作品”入口。
- **九角色 IP 舞台**：支持点击舞台、箭头、角色选择点、左右拖动及键盘切换；角色与背景色同步过渡。
- **独立项目案例**：以大图、角色场景、多规格适配和原稿展示组织不同类型的作品。
- **手机框长图预览**：两张活动 H5 可独立滚动，支持阅读进度、回到顶部和查看原稿。
- **清晰的合作入口**：工作经历、能力与服务、简历下载、邮箱联系与复制。
- **兼顾可访问性的交互**：跳至正文、可见键盘焦点、选中状态反馈、两级 Esc 关闭、焦点返回和减少动态偏好。

## 内容结构

| 首页板块 | 展示内容 |
| --- | --- |
| 动态首页 | 个人定位、滚动视频、作品入口 |
| 关于我与工作经历 | 设计背景、工作经历、简历信息 |
| Project Zero | 精选案例、分类筛选、九角色 IP 舞台 |
| 能力与合作服务 | 品牌视觉、IP 文创、Campaign、动态内容 |
| 联系我 | 邮箱、合作方向与简历下载 |

Project Zero 当前包含四个独立详情页：

| 项目 | 展示重点 |
| --- | --- |
| 明日之星 | IP 文创、沙盘产品与实体组件 |
| 品牌 VI | 标志、色彩、字体规范与品牌应用 |
| 未来家族共创营 | 活动主视觉、传播长图、手册与场景应用 |
| 包装设计 | BabyJoy 九仔盲盒、角色系列、包装展开与印刷稿 |

## 技术实现

整体采用**静态网站＋局部 React 组件**的结构：日常内容由 HTML、CSS 和 JavaScript 承载，复杂交互由独立组件实现。

| 层面 | 使用技术 |
| --- | --- |
| 首页与项目详情 | HTML、CSS、原生 JavaScript、ES Modules |
| IP 舞台与手机预览 | React 18、TypeScript |
| 组件样式与图标 | Tailwind CSS、Lucide React |
| 组件构建 | Vite |
| 动效 | CSS 过渡、Web Animations API、滚动驱动视频 |
| 本地与容器运行 | Node.js 原生 HTTP 服务，支持视频 Range 请求 |
| 发布 | 静态托管、GitHub Pages 工作流或 Node 托管 |

前台无需数据库。图片、视频、简历和已构建组件均随仓库保存；字体通过 Google Fonts 加载，并设置系统字体回退。

## 快速开始

需要 **Node.js 22.13 或更高版本**。下载或克隆仓库后，在仓库根目录运行：

```bash
npm start
```

打开 **http://localhost:3000/**。

当前网站已包含构建产物，启动时无需安装第三方依赖。也可以直接使用：

```bash
node scripts/serve.mjs
```

请通过 HTTP 预览，直接双击 HTML 打开的 `file://` 地址无法完整支持项目详情模块。

## 常用命令

| 命令 | 用途 |
| --- | --- |
| `npm start` | 启动网站，默认端口为 3000 |
| `npm run dev` | 启动同一个静态服务；不提供热更新 |
| `npm run check` | 检查本地资源引用与详情页完整性 |
| `npm run build` | 校验已包含的静态产物，不重新编译组件 |
| `npm run build:components` | 在依赖安装后，重新构建两套 React 组件并校验 |

修改 React／TypeScript 组件时，需要额外安装 **pnpm 11.25.0**：

```bash
pnpm --dir jiuzai install --frozen-lockfile
pnpm --dir jiuzai run build:all
npm run check
```

修改静态 HTML、CSS 或项目详情 JavaScript 时，不需要执行组件构建。

## 目录导航

```text
.
├── site/                     可直接发布的静态网站
│   ├── index.html            首页结构
│   ├── app.js                项目数据与公共交互
│   ├── assets/               图片、视频与简历
│   ├── *-case.js / .css       四个项目的详情模块
│   ├── jiuzai/               IP 舞台构建产物
│   └── camp-phone/           手机预览构建产物
├── jiuzai/                   React 组件工程及依赖锁文件
│   └── src/                  IP 舞台、角色数据与手机预览源码
├── scripts/                  静态服务器与资源检查工具
├── .github/workflows/        GitHub Pages 发布流程
├── .10k/                     截图与设计过程记录
├── prepare-*.py              原始设计素材的导出工具
├── PRODUCT.md                产品定位与内容原则
├── DESIGN.md                 视觉与交互规范
└── DEPLOYMENT.md             部署、备份与维护指南
```

## 从哪里开始阅读源码

- 想了解页面结构：[site/index.html](site/index.html)。
- 想修改项目名称、分类或封面：[site/app.js](site/app.js)。
- 想研究角色切换：[jiuzai/src/main.tsx](jiuzai/src/main.tsx) 与 [image-data.ts](jiuzai/src/image-data.ts)。
- 想研究手机框长图：[camp-phone.tsx](jiuzai/src/camp-phone.tsx)。
- 想了解设计决策：[DESIGN.md](DESIGN.md) 与 [PRODUCT.md](PRODUCT.md)。

`prepare-*.py` 仅用于从原始设计档案重新导出资源，部分脚本依赖本机的原素材目录。网站运行与上线不依赖这些脚本，实际使用的导出文件均已包含。

## 如何部署

**静态托管直接发布 `site/` 目录即可。** 仓库已提供 GitHub Pages 工作流；Coze 导入、容器启动、端口设置与备份步骤见 [部署与维护指南](DEPLOYMENT.md)。

上传 GitHub 时，请先解压备份包，再提交目录内文件；仅把 ZIP 上传到仓库，不会自动得到可运行的网站。

## 当前状态与后续方向

目前已对桌面及 390px、320px 手机视口进行人工检查，并验证资源引用、项目详情和主要键盘操作。这不代表通过完整无障碍认证或所有设备测试。

后续计划包括：内容管理后台、项目图片与文案在线更新、媒体资源管理，以及正式域名与线上性能优化。**这些功能目前尚未包含在代码库中。**

## 交流与使用边界

欢迎反馈布局、交互或兼容性问题。提交问题时，请附上浏览器、屏幕尺寸、复现步骤和截图，方便定位。

设计合作与全职机会：**Yara 陈燕红** · [1291673097@qq.com](mailto:1291673097@qq.com)。

本仓库尚未为整体代码和设计作品授予统一开源许可。公开代码不等于授权使用其中的项目作品、照片、视频或简历；如需复用，请先与作者沟通。第三方软件遵循各自许可证，详见 [第三方说明](THIRD-PARTY-NOTICES.md) 与 [licenses/](licenses/)。
