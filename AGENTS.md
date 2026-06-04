
## 根目录文件
| 文件 | 说明 |
|------|------|
| `index.md` | VitePress 首页/Hero page，展示 EchoMusic 简介和导航入口 |
| `README.md` | 项目说明，介绍文档仓库用途、本地开发方法和贡献指南 |
| `_redirects` | 单页应用路由重定向配置 |
| `package.json` | Node.js 项目配置（VitePress + Mermaid + Tabs 插件） |
| `pnpm-lock.yaml` | pnpm 依赖锁定文件 |
| `LICENSE` | 开源许可证文件 |

## 文件夹结构详述

### `.vitepress/` — VitePress 站点配置
| 文件/文件夹 | 说明 |
|-------------|------|
| `config.mts` | VitePress 核心配置：导航栏、侧边栏、多语言（中文/English）、搜索、markdown 插件 |
| `theme/` | 自定义主题目录 |
| `theme/index.ts` | 主题入口 |
| `theme/style.css` | 自定义样式 |
| `components/` | 自定义 Vue 组件（如 DownloadButton） |

### `guide/` — 用户使用指南（简体中文）
| 文件 | 说明 |
|------|------|
| `index.md` | 使用指南总览 |
| `getting-started.md` | 下载安装与快速开始 |
| `playback.md` | 播放控制与队列管理 |
| `music-discovery.md` | 音乐发现与推荐 |
| `search.md` | 搜索功能 |
| `lyrics.md` | 歌词系统 |
| `audio.md` | 音频增强设置 |
| `personal-fm.md` | 私人 FM |
| `music-recognition.md` | 听歌识曲 |
| `song-detail.md` | 歌曲详情与评论 |
| `settings.md` | 偏好设置 |
| `faq.md` | 常见问题 |

### `develop/` — 开发文档（简体中文）
| 文件 | 说明 |
|------|------|
| `index.md` | 开发指南总览 |
| `architecture.md` | 架构设计 |
| `project-structure.md` | 项目结构 |
| `local-dev.md` | 本地开发环境搭建 |
| `native-addons.md` | Rust NAPI 原生模块 |
| `build.md` | 编译与构建 |
| `contributing.md` | 贡献指南 |
| `api.md` | API 参考 |

### `features/` — 功能介绍
### `changelog/` — 更新日志
### `community/` — 社区页面

### `en/` — 英文版文档
en/ 目录下的结构与中文版完全镜像，包含 guide/（使用指南）、develop/（开发文档）、features/（功能介绍）、changelog/（更新日志）、community/（社区页面）等子目录。

> ⚠️ **注意**：en/ 英文文档是通过翻译中文内容得来，应最大程度与中文内容保持同步。

### `public/` — 静态资源
| 文件夹 | 说明 |
|--------|------|
| `title_img/` | 首页标题图片 |
| `images/` | 文档图片（截图、示意图） |
