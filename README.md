# EchoMusic 文档

本仓库为 EchoMusic 的官方 Wiki 文档。EchoMusic 是一款开源、简洁、高颜值的酷狗概念版第三方客户端，专为桌面端打造。

## 关于文档

此文档站点使用 [VitePress](https://vitepress.dev/) 构建，涵盖 EchoMusic 的使用指南、功能介绍、开发文档和社区信息。

## 文档目录

- **使用指南** — 涵盖下载安装、播放控制、音乐发现、搜索、歌词、音频设置等
- **功能介绍** — 全方位的功能特性展示
- **开发文档** — 架构设计、项目结构、本地开发、原生模块、构建打包、API 参考
- **更新日志** — 版本更新内容记录
- **社区** — 交流群、GitHub、贡献指南

## 本地开发

```bash
# 安装依赖
pnpm install

# 启动开发服务器
pnpm docs:dev

# 构建生产版本
pnpm docs:build

# 预览生产版本
pnpm docs:preview
```

## 贡献

欢迎参与文档贡献！如果你想修改文档，请 fork 后修改并提交 PR。

如果你想要添加新文档，在 fork 后将文档放入对应目录，修改各级 `index.md` 使其包含你的文档，并在 `.vitepress/config.mts` 中配置导航，随后提交 PR。
