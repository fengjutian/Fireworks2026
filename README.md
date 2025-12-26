# Fireworks 2026

一个使用 Three.js 实现的高性能烟花效果，并带有深沉的爆炸低音音效。支持可视化参数调节、后期泛光效果、自动/手动发射等特性。

## 运行
- 使用本地 HTTP 服务打开页面，避免 `file://` 的模块与跨域限制：
  - Python：`python -m http.server 5500` 然后访问 `http://localhost:5500/`
  - Node.js：`npx http-server -p 5500` 或 `npx serve`
- 打开页面后点击覆盖层以初始化音频并开始首次烟花。

## 依赖
- 使用 CDN 加载：
  - `three@0.160.0` 与 `three/addons`（`index.js` 顶部导入，见 `c:\Users\26401\Desktop\Fireworks2026\index.js:1-5`）
  - `es-module-shims` 作为 import maps polyfill（`c:\Users\26401\Desktop\Fireworks2026\index.html:8`）
- 导入映射在 `<head>` 中并位于模块脚本之前（`c:\Users\26401\Desktop\Fireworks2026\index.html:9-16`）。

## 文件
- `index.html`：页面结构与导入映射、polyfill、入口脚本
- `index.css`：基础样式与覆盖层、GUI 位置
- `index.js`：场景、后期处理、烟花逻辑、深低音音频系统

## 使用
- 覆盖层：点击后初始化音频并隐藏覆盖层
- GUI 控件（右下角“Settings”）：
  - `Particles`：`particleCount`、`particleSize`、`fadeSpeed`
  - `Physics`：`explosionForce`、`hoverDuration`、`gravity`
  - `Deep Audio`：`soundEnabled`、`volume`
- 自动发射：`CONFIG.autoLaunch` 与 `CONFIG.launchInterval`
- 窗口变化：自动适配画布与后期分辨率

## 性能建议
- 降低 `particleCount` 或 `bloomStrength`
- 将 `renderer.setPixelRatio` 保持在 ≤ 1.5
- 关闭或降低 `hoverDuration` 以减少悬停计算

## 许可
- `package.json` 中设置为 `ISC` 许可

## 致谢
- [three.js](https://threejs.org)
