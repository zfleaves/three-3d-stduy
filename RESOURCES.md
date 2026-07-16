# Three.js 3D 开发 学习资源

## Knowledge

### 官方文档（一级资源）
- [Three.js 官方文档](https://threejs.org/docs/index.html#manual/zh/introduction)
  中文手册，涵盖所有核心 API。使用场景：查阅任何 API 用法时的第一参考。
- [Three.js 官方示例](https://threejs.org/examples/)
  数百个官方 demo，每个功能都有对应示例代码。使用场景：学习具体功能时先看官方示例。
- [WebGL2 规范](https://registry.khronos.org/webgl/specs/latest/2.0/)
  Khronos 官方 WebGL2 规范。使用场景：Lv1 学习底层 API 时参考。

### 书籍
- 《WebGL 编程指南》— Kouichi Matsuda & Rodger Lea
  WebGL 入门圣经，手把手教渲染管线。使用场景：Lv1 阶段系统学习 WebGL 基础。
- 《Three.js 开发指南》— Jos Dirksen
  Three.js 实战书籍，覆盖从基础到高级。使用场景：Lv2-Lv3 阶段参考。

### 文章教程
- [Three.js Shader 入门教程（一）— 古柳（掘金）](https://juejin.cn/post/7233359844974182437)
  **Lv4 Shader 核心参考**，从几何体顶点→UV→ShaderMaterial→GLSL 的平缓渐进路径。
- [从零开始学图形学：MVP Transformation](https://zhuanlan.zhihu.com/p/343532009)
  MVP 变换详解。使用场景：Lv4.3 顶点着色器学习。
- [图形学：MVP变换概述](https://zhuanlan.zhihu.com/p/551648397)
  另一篇 MVP 变换文章，互为补充。
- [计算机图形学：齐次坐标与 MVP 矩阵变换](https://zhuanlan.zhihu.com/p/261097735)
  深入理解齐次坐标在 MVP 中的作用。

### 视频教程（B站）
- 李超：WebGL 原生零基础入门 — Lv1 底层基础
- 老陈说编程：ThreeJS 入门到数字孪生 — 全阶段实战
- 十里青山：ThreeJS 系统进阶课 — Lv3-Lv4 进阶
- 技术蛋老师：Shader 着色器入门 — Lv4 核心
- 进华：three.js教程-从入门到入门 — 简洁清晰，全阶段参考
- 犹他大学计算机图形学课程（2020秋，B站中英字幕）— MVP 变换深入理解

### Shader 专项资源（💰 Lv4 薪资分水岭核心）

- [古柳·Three.js Shader 入门教程（一）](https://juejin.cn/post/7233359844974182437)
  几何体顶点→UV→ShaderMaterial→GLSL 渐进路径。**Lv4 核心参考**。
- 古柳·Three.js Shader 入门教程（二-五）
  系列后续：内置变量、纹理采样、噪声、后处理实战。
- 古柳·Three.js Shader 着色器基础（3篇）
  attribute/uniform/varying、纹理、噪声。**Lv4.3-4.7 参考**。
- [The Book of Shaders](https://thebookofshaders.com/)（中文版）
  **GLSL 圣经**，交互式学习。从形状→图案→噪声→分形，Lv4 全程参考。
- [Shadertoy](https://www.shadertoy.com/)
  海量 Shader 源码社区。**学习方式：搜索 dissolve/glow/noise 等关键词，模仿源码**。
- [Inigo Quilez 博客](https://iquilezles.org/)
  Ray Marching、SDF、噪声算法。**进阶必读**，Lv4 完成后可深入。
- 阳轩·Three.js 进阶之旅（掘金专栏）
  Shader 着色器入门 + 光源 + 粒子 + 性能优化，全阶段参考。

### 工具链
- [Blender](https://www.blender.org/) — 开源 3D 建模软件，模型减面、UV、GLB 导出
- [glTF-Transform](https://gltf-transform.dev/) — glTF 模型压缩/优化 CLI
- [Draco](https://github.com/google/draco) — Google 的 3D 网格压缩库
- [Cannon-es](https://github.com/pmndrs/cannon-es) — 3D 物理引擎（JS 版 Cannon.js 的维护分支）

### 进阶参考
- [Learn OpenGL](https://learnopengl.com/) — 虽然面向 OpenGL，但 Shader 和图形学原理通用
- [The Book of Shaders](https://thebookofshaders.com/) — 交互式 Shader 入门，Lv4 必备
- [WebGPU 规范](https://www.w3.org/TR/webgpu/) — 下一代 Web 图形 API，了解趋势
- [Codepen 古柳示例](https://codepen.io/GuLiu/pen/poBBEgP) — 掘金 Shader 文章配套代码
- 公众号「牛衣古柳」— 回复 `learn three.js` 获取《Three.js 开发指南》PDF

## Wisdom (Communities)

- [Three.js 官方论坛](https://discourse.threejs.org/)
  最活跃的 Three.js 社区，核心开发者常驻。使用场景：遇到疑难 bug 时提问。
- [Three.js Discord](https://discord.gg/threejs)
  实时讨论，适合快速问题交流。
- [r/threejs](https://reddit.com/r/threejs)
  Reddit 社区，作品展示和技巧分享。
- 国内：掘金 Three.js 标签、知乎 Three.js 话题
  中文技术文章和项目经验分享。

## Gaps

- 缺少系统性的 Three.js + Vue3/React 工程化实战教程
- 数字孪生/智慧城市方向的完整开源项目参考较少
- WebGPU 中文学习资料匮乏