# Three.js 3D 开发学习计划 v3 — 平缓曲线 · 多Demo · 实战驱动

> 设计原则：**先会用（建立信心）→ 再理解（深入原理）→ 后优化（高阶能力）→ 终落地（商业项目）**
> 参考来源：`docs/base.md` 五级体系 + BOSS直聘招聘要求 + [掘金·古柳 Three.js Shader 入门](https://juejin.cn/post/7233359844974182437)

---

## 🏔️ 学习曲线设计

```
难度
 ↑
 │                                          ██ Lv5 商业项目
 │                                      ████
 │                                  ████
 │                              ████ Lv4 Shader+性能（掘金文章核心参考）
 │                          ████
 │                      ████
 │               ████████ Lv3 模型+交互
 │           ████
 │       ████ Lv2 深入理解（含几何体内部结构、UV 铺垫）
 │   ████
 │███ Lv1 快速上手（信心区）
 └──────────────────────────────────────────→ 时间
   3天  1周  2周  3周  4周  6周  8周  10周+
```

---

## 核心改进（v3 更新）

| 版本 | 改进 |
|------|------|
| v1→v2 | 从 WebGL 底层起步 → Three.js 高层起步，平缓曲线 |
| v2→v3 | 新增"几何体内部结构"桥梁，让 Shader 学习从"理解数据"开始而非"写 GLSL" |

### 🆕 掘金文章核心贡献

掘金·古柳的 Shader 入门教程提供了一个**极其平缓的 Shader 学习路径**：

```
理解几何体顶点 → 认识顶点属性(position/uv/normal) → UV坐标可视化 → 替换ShaderMaterial → GLSL语法 → 片元着色器
```

这个路径被整合到 Lv2（铺垫）和 Lv4（核心）中，解决了"从 Three.js API 到写 Shader 之间鸿沟太大"的问题。

---

## Lv1 — Three.js 快速上手（3天，信心建立期）

> **目标**：会用 Three.js 搭场景，感受到"写几行代码就能出3D效果"的成就感
> **难度**：★☆☆☆☆

### 1.1 第一个3D场景：旋转的立方体（30分钟）
**Demo**: `demo-01-hello-cube.html` ✅
- 引入 Three.js CDN
- 创建场景、相机、渲染器
- 添加一个立方体，让它旋转
- **收获**：10行代码看到3D效果

### 1.2 认识几何体家族（30分钟）
**Demo**: `demo-02-geometries.html` ✅
- 立方体、球体、圆柱体、圆锥体、圆环、平面
- 每个几何体的关键参数（长宽高、半径、分段数）
- **收获**：知道 Three.js 能创建哪些基本形状

### 1.3 光影魔法（30分钟）
**Demo**: `demo-03-lights.html` ✅
- 环境光、平行光、点光源、聚光灯、半球光
- 无光 vs 有光对比
- **收获**：理解光照对3D场景真实感的重要性

### 1.4 鼠标控制视角（30分钟）
**Demo**: `demo-04-orbit-controls.html` ✅
- OrbitControls：拖拽旋转、滚轮缩放、右键平移
- **收获**：让场景可交互

### 1.5 材质初探（45分钟）
**Demo**: `demo-05-materials.html` ✅
- MeshBasicMaterial / MeshStandardMaterial / MeshPhongMaterial / MeshNormalMaterial / wireframe
- 粗糙度 × 金属度 = 所有真实材质
- **收获**：理解材质决定物体外观

### 1.6 🎯 综合项目：3D 产品展示台（1小时）
**Demo**: `project-01-product-showcase.html` ✅
- 多几何体排列 + 光照阴影 + 鼠标交互 + 颜色切换
- **收获**：第一个完整小项目

---

## Lv2 — Three.js 深入理解（7-10天）

> **目标**：理解 Three.js 核心概念，**初步接触几何体内部结构**，为 Shader 做铺垫
> **难度**：★★☆☆☆

### 2.1 🔍 几何体内部结构：点线面体（45分钟）⭐ 新增
**Demo**: `demo-06-geometry-inside.html`
- 开启 `wireframe: true` 观察几何体的三角形组成
- `console.log(geometry)` 查看顶点数据
- 理解"点→线→三角形→面"的构成原理
- 平面 = 4个顶点 + 2个三角形
- `geometry.attributes`：position、uv、normal
- `count`（顶点数）和 `itemSize`（每个属性的维度）
- **收获**：**建立对几何体内部数据的直观认知（Shader 学习的关键前提）**

### 2.2 📐 UV 纹理坐标：从顶点到纹理（45分钟）⭐ 新增
**Demo**: `demo-07-uv-coordinates.html`
- UV 概念：u 从左到右 (0→1)，v 从下到上 (0→1)
- 用颜色可视化 UV 坐标（R=u, G=v, B=0）
- 理解"GPU 自动插值三角形内部像素的 UV 值"
- 平面中心 UV = (0.5, 0.5)
- UV 与纹理贴图的关系：UV 告诉 GPU"贴图的哪个位置贴到哪个顶点"
- **收获**：**理解 UV 是纹理贴图的基础，也是 Shader 中最重要的内置变量之一**

### 2.3 坐标系统与变换（45分钟）
**Demo**: `demo-08-transforms.html`
- position / rotation / scale
- 世界坐标 vs 局部坐标，父子关系（Group）
- 可视化坐标轴
- **收获**：精确控制物体位置

### 2.4 纹理贴图实战（45分钟）
**Demo**: `demo-09-textures.html`
- 颜色贴图（基于 2.2 的 UV 理解，水到渠成）
- 法线贴图（凹凸感）、环境贴图（反射）
- 贴图加载与跨域处理
- **收获**：让物体有真实质感

### 2.5 动画系统（45分钟）
**Demo**: `demo-10-animation.html`
- requestAnimationFrame 原理、缓动函数
- 物体动画 + 相机动画（漫游）
- **收获**：让场景动起来

### 2.6 粒子系统（45分钟）
**Demo**: `demo-11-particles.html`
- Points + PointsMaterial
- 下雨/下雪/星空效果
- **收获**：掌握粒子特效

### 2.7 阴影完全指南（45分钟）
**Demo**: `demo-12-shadows.html`
- 阴影完整配置、软阴影 vs 硬阴影
- **收获**：掌握阴影系统

### 2.8 🎯 综合项目：3D 房间漫游（2小时）
**Demo**: `project-02-room-tour.html`
- 几何体搭建房间 + 光影阴影 + 第一人称漫游（WASD）+ 粒子灰尘
- **收获**：完整3D场景搭建能力

---

## Lv3 — 模型加载与交互（7-10天）

> **目标**：加载外部模型，实现交互，做出"像产品"的3D页面
> **难度**：★★★☆☆

### 3.1 GLTF/GLB 模型加载（1小时）
**Demo**: `demo-13-load-model.html`
- 加载 GLB 模型、调整大小位置、加载进度、失败处理
- **收获**：引入外部3D资源

### 3.2 模型动画播放（1小时）
**Demo**: `demo-14-model-animation.html`
- 骨骼动画播放、切换、混合（淡入淡出）
- **收获**：让模型动起来

### 3.3 鼠标拾取与交互（1小时）
**Demo**: `demo-15-raycaster.html`
- Raycaster 射线检测、悬浮高亮、点击选中
- **收获**：3D场景核心交互能力

### 3.4 天空盒与环境（30分钟）
**Demo**: `demo-16-skybox.html`
- 天空盒、雾化、背景渐变
- **收获**：营造场景氛围

### 3.5 场景管理（45分钟）
**Demo**: `demo-17-scene-management.html`
- Group 分组、显示/隐藏、场景切换、克隆
- **收获**：管理复杂场景

### 3.6 🎯 综合项目：3D 产品展示官网（3小时）
**Demo**: `project-03-product-page.html`
- GLB模型 + PBR材质 + 颜色切换 + 动画 + 响应式
- **收获**：可上线的产品展示页

---

## Lv4 — Shader 着色器 + 性能优化（15-20天）⭐ 薪资分水岭

> **目标**：彻底掌握 Shader，从"API调用者"变成"能写自定义特效的3D工程师"
> **参考**：掘金·古柳「Three.js Shader 入门」系列 + 《The Book of Shaders》+ Shadertoy
> **难度**：★★★★☆ · **这是整个学习计划中最重要的一级，决定了你的薪资天花板**

### 💰 为什么 Shader 是分水岭？

| 能力 | 市场定位 | 薪资 |
|------|---------|------|
| 只会用 Three.js API | 初级 3D 前端（可替代性强） | 10k-18k |
| 能写自定义 Shader 特效 | 中级 3D 前端（有竞争力） | 15k-25k |
| Shader + 性能优化 + 架构 | 高级 3D 前端（稀缺） | 25k-50k+ |
| Shader + WebGPU + 图形学 | 专家/架构师（极度稀缺） | 50k-80k |

### 🔑 Lv4 Shader 学习路径

```
Lv2已铺垫(几何体内部结构+UV) → 复习顶点属性 → 替换ShaderMaterial
→ GLSL语法速成 → attribute/uniform/varying 数据传递
→ 顶点着色器MVP变换 → 片元着色器UV创意
→ 纹理采样 → 噪声算法 → 经典特效
→ 后处理 → 性能优化 → 综合实战
```

### 📚 Shader 核心参考资料

| 资源 | 类型 | 覆盖内容 |
|------|------|---------|
| [古柳·Shader入门教程(一)](https://juejin.cn/post/7233359844974182437) | 文章 | 几何体→UV→ShaderMaterial→GLSL基础 |
| 古柳·Shader入门教程(二-五) | 系列 | 内置变量、纹理、噪声、实战 |
| 古柳·着色器基础(3篇) | 系列 | attribute/uniform/varying、纹理采样、噪声 |
| [The Book of Shaders](https://thebookofshaders.com/) | 交互书 | GLSL 圣经，从形状到噪声到分形 |
| [Shadertoy](https://www.shadertoy.com/) | 平台 | 海量 Shader 源码，模仿学习 |
| [Inigo Quilez](https://iquilezles.org/) | 博客 | Ray Marching、SDF、噪声（进阶） |
| 阳轩·Three.js 进阶之旅 | 掘金专栏 | Shader + 光源 + 粒子 + 性能 |

---

### 🎯 Shader 专项（核心 10 个 Demo）⭐⭐⭐

### 4.1 复习顶点属性 + 第一个 ShaderMaterial（1小时）
**Demo**: `demo-18-first-shader.html`
- 回顾 Lv2.1 的 `geometry.attributes`（position、uv、normal）
- 用 `ShaderMaterial` 替换 `MeshBasicMaterial`
- 写最简单的红色片元着色器：`gl_FragColor = vec4(1.0, 0.0, 0.0, 1.0);`
- 顶点着色器最小结构：`gl_Position = projectionMatrix * modelViewMatrix * vec4(position, 1.0);`
- 理解 ShaderMaterial vs RawShaderMaterial 的区别
- **参考**：古柳·Shader入门教程(一)
- **收获**：从内置材质到自定义 Shader 的第一步

### 4.2 GLSL 语言速成（1小时）
**Demo**: `demo-19-glsl-basics.html`
- 数据类型：float、int、bool、vec2、vec3、vec4、mat3、mat4
- 向量分量：`.x .y .z .w` / `.r .g .b .a` / `.s .t .p .q`
- 向量运算：逐分量计算、`vec3(vec2(0.5), 1.0)` 灵活组合
- 内置函数：`mix()、step()、smoothstep()、clamp()、fract()、length()、distance()、dot()、cross()、normalize()、sin()、cos()`
- 颜色范围：0.0-1.0（超出被截取）、语句必须分号
- **参考**：《The Book of Shaders》第1-3章
- **收获**：掌握 GLSL 基本语法和核心内置函数

### 4.3 数据传递：attribute、uniform、varying（1.5小时）
**Demo**: `demo-20-shader-data-flow.html`
- **attribute**：每个顶点不同的数据（position、uv、normal、color）
- **uniform**：所有顶点相同的数据（时间、鼠标位置、分辨率、纹理）
- **varying**：顶点着色器 → 片元着色器的数据桥梁（自动插值）
- 实战：用 uniform 传时间做动画，用 varying 传颜色做渐变
- **参考**：古柳·着色器基础(一) attribute/uniform/varying
- **收获**：理解 Shader 中数据如何流动

### 4.4 顶点着色器与 MVP 变换（1.5小时）
**Demo**: `demo-21-vertex-shader.html`
- MVP 变换全流程：Model → View → Projection
- `modelMatrix`、`viewMatrix`、`modelViewMatrix`、`projectionMatrix`
- 顶点扰动：`position.y += sin(position.x * 3.0 + uTime) * 0.1;`
- 顶点变形：波纹、膨胀、扭曲
- **参考**：知乎 MVP 文章 + 犹他大学图形学课程
- **收获**：理解顶点着色器如何控制物体形状

### 4.5 片元着色器 + UV 创意（1.5小时）
**Demo**: `demo-22-fragment-uv.html`
- UV 渐变：`gl_FragColor = vec4(vUv.x, vUv.y, 0.0, 1.0);`
- 重复条纹：`step(0.5, fract(vUv.x * 5.0))`
- 圆形/环形：`length(vUv - 0.5)`、`smoothstep()`
- 网格/棋盘：`fract()` 组合
- 颜色混合：`mix(color1, color2, factor)`
- **参考**：《The Book of Shaders》第4-5章（形状与图案）
- **收获**：用 UV 坐标创造丰富的 2D 图案

### 4.6 纹理采样与图像处理（1.5小时）
**Demo**: `demo-23-shader-texture.html`
- 将纹理传入 Shader：`uniform sampler2D uTexture;`
- 纹理采样：`texture2D(uTexture, vUv);`
- 图像滤镜：灰度、反色、亮度/对比度/饱和度
- 模糊效果：多次采样取平均
- 纹理混合：多纹理叠加
- **参考**：古柳·着色器基础(二) 纹理
- **收获**：在 Shader 中处理纹理和图像

### 4.7 噪声算法：随机与秩序（2小时）⭐
**Demo**: `demo-24-noise.html`
- 随机函数：`fract(sin(dot(uv, vec2(12.9898, 78.233))) * 43758.5453)`
- 值噪声（Value Noise）：随机 + 平滑插值
- 柏林噪声（Perlin Noise）：自然的随机感
- Simplex Noise：柏林噪声的优化版
- 分形布朗运动（fBm）：多层噪声叠加
- 应用：云朵、火焰、地形、大理石纹理
- **参考**：古柳·着色器基础(三) 噪声 + 《The Book of Shaders》第11-13章
- **收获**：噪声是 Shader 最重要的算法之一，开启无限创意

### 4.8 经典 Shader 特效（2小时）
**Demo**: `demo-25-shader-effects.html`
- 溶解效果（dissolve）：`discard` + noise 阈值
- 波纹效果（ripple）：`sin(distance(uv, center) * freq + time)`
- 描边/轮廓（outline）：Fresnel 效果 `1.0 - abs(dot(normal, viewDir))`
- 霓虹发光（glow）：`smoothstep()` + 多层叠加
- 全息效果（hologram）：扫描线 + 透明度 + 边缘发光
- 故障效果（glitch）：随机偏移色块
- **参考**：Shadertoy 搜索 dissolve/glow/hologram 源码
- **收获**：掌握 6 种常用 Shader 特效

### 4.9 后处理特效（1.5小时）
**Demo**: `demo-26-postprocessing.html`
- EffectComposer 管线：多个 Pass 串联
- UnrealBloomPass：辉光（Bloom）
- AfterimagePass：拖尾残影
- ShaderPass：自定义后处理 Shader
- 画面调色：LUT 颜色查找表
- **参考**：古柳·Shader入门教程(五) 后期处理
- **收获**：提升画面品质到电影级

### 4.10 🎯 综合项目：Shader 特效秀（3小时）
**Demo**: `project-04-shader-show.html`
- 6+ 自定义 Shader 特效组合
- 辉光后处理 + 鼠标交互
- 噪声驱动动画
- 性能优化（60fps）
- **收获**：展示技术深度的作品集项目

---

### ⚡ 性能优化专项（3个 Demo）

### 4.11 渲染性能优化（1.5小时）
**Demo**: `demo-27-performance.html`
- 1000个物体：普通 Mesh vs InstancedMesh（帧率对比）
- FPS 监控面板
- 几何体合并（BufferGeometryUtils.mergeGeometries）
- 视锥剔除（Frustum Culling）
- LOD（多细节层次）
- **收获**：让海量物体跑 60fps

### 4.12 资源与内存优化（1小时）
**Demo**: `demo-28-resource-optimization.html`
- 贴图 2 的幂次方规范
- 纹理压缩（KTX2/Basis）
- `dispose()` 资源销毁
- SPA 路由切换时的资源清理
- 内存泄漏检测
- **收获**：避免线上内存泄漏事故

### 4.13 物理引擎（1.5小时）
**Demo**: `demo-29-physics.html`
- Cannon-es 重力+碰撞+弹跳
- 多米诺骨牌效果
- **收获**：场景有物理真实感

---

## Lv5 — 工程化与商业项目（持续）

> **目标**：从零到上线交付完整商业项目
> **难度**：★★★★★

### 5.1 工程化搭建（2小时）
- Vite + TypeScript 项目模板
- 目录结构、全局单例管理

### 5.2 资源管理（1.5小时）
- 预加载队列、加载进度条、异常兜底

### 5.3 前端框架集成（2小时）
- React + react-three-fiber 或 Vue3 + TresJS

### 5.4 移动端适配（1.5小时）
- 触摸手势、设备性能检测、高低配降级

### 5.5 🎯 毕业项目（二选一）
1. **数字孪生园区**：建筑模型 → 数据点位 → 弹窗交互 → 视角漫游 → 线上部署
2. **3D 互动产品官网**：产品展示 → 材质切换 → 特效美化 → 移动端适配

---

## 📊 总 Demo 数量统计

| 阶段 | 小 Demo | 综合项目 | 合计 | 说明 |
|------|---------|---------|------|------|
| Lv1 快速上手 | 5 | 1 | 6 | 全部 ✅ |
| Lv2 深入理解 | 7 | 1 | 8 | 新增几何体内部结构+UV |
| Lv3 模型交互 | 5 | 1 | 6 | — |
| Lv4 Shader+性能 | 12 | 1 | **13** | 重构：Shader 10专项+3性能+1项目 |
| Lv5 工程化 | 4 | 1 | 5 | — |
| **总计** | **33** | **5** | **38** | |

---

## 🎯 学习节奏（建议）

| 天数 | 内容 | 状态 |
|------|------|------|
| Day 1 | Lv1.1 Hello Cube + Lv1.2 几何体 | ✅ |
| Day 2 | Lv1.3 光影 + Lv1.4 鼠标控制 | ☐ |
| Day 3 | Lv1.5 材质 + Lv1.6 🎯 产品展示台 | ☐ |
| Day 4-5 | Lv2.1 几何体内部结构 + Lv2.2 UV坐标 | ☐ |
| Day 6-7 | Lv2.3 坐标变换 + Lv2.4 纹理贴图 | ☐ |
| Day 8-9 | Lv2.5 动画 + Lv2.6 粒子 | ☐ |
| Day 10-11 | Lv2.7 阴影 + Lv2.8 🎯 房间漫游 | ☐ |
| Day 12-14 | Lv3.1 模型加载 + Lv3.2 动画 | ☐ |
| Day 15-17 | Lv3.3 鼠标拾取 + Lv3.4 天空盒 + Lv3.5 场景管理 | ☐ |
| Day 18-19 | Lv3.6 🎯 产品展示官网 | ☐ |
| Day 20-22 | Lv4.1 第一个ShaderMaterial + Lv4.2 GLSL速成 + Lv4.3 数据传递 | ☐ |
| Day 23-26 | Lv4.4 顶点着色器 + Lv4.5 片元UV创意 + Lv4.6 纹理采样 | ☐ |
| Day 27-30 | Lv4.7 噪声算法 + Lv4.8 经典特效 | ☐ |
| Day 31-33 | Lv4.9 后处理 + Lv4.10 🎯 Shader特效秀 | ☐ |
| Day 34-37 | Lv4.11 性能优化 + Lv4.12 资源优化 + Lv4.13 物理引擎 | ☐ |
| Week 8-12+ | Lv5 工程化 + 毕业项目 | ☐ |

---

## ⚠️ 核心原则

1. **每个 Demo 都要亲手敲代码**，不要复制粘贴
2. **先跑通，再理解**，最后才优化
3. **遇到报错是好事**，排查过程学得最扎实
4. **每完成一个 Demo 就 commit 一次**，积累 GitHub 贡献
5. **不要跳级**，但同一级内可以自由调整顺序
6. **Lv3 完成后就可以投简历试水**，边学边面
7. **Shader 学习从"理解数据"开始**：先看懂 geometry.attributes，再碰 GLSL 代码

---

## 📚 关键参考资源

### 掘金文章（本次参考）
- [Three.js Shader 入门教程（一）— 古柳](https://juejin.cn/post/7233359844974182437) — Lv4 Shader 部分的核心参考

### 图形学原理
- [从零开始学图形学：MVP Transformation](https://zhuanlan.zhihu.com/p/343532009)
- [图形学：MVP变换概述](https://zhuanlan.zhihu.com/p/551648397)
- [计算机图形学：齐次坐标与 MVP 矩阵变换](https://zhuanlan.zhihu.com/p/261097735)

### 视频教程
- B站「进华」：three.js教程-从入门到入门（简洁清晰）
- 犹他大学计算机图形学课程（2020秋，B站中英字幕）— MVP 变换理解

### 在线代码
- [Codepen 示例](https://codepen.io/GuLiu/pen/poBBEgP) — 掘金文章配套代码