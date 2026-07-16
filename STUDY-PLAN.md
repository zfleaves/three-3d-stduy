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

### 2.8 PBR 材质深入（45分钟）⭐ 新增
**Demo**: `demo-13-pbr-deep.html`
- 环境贴图对金属反射的影响（无环境贴图→金属发黑）
- 粗糙度×金属度×环境贴图的三角关系
- roughnessMap / metalnessMap / normalMap / aoMap 用法
- MeshStandardMaterial 全部参数详解
- **收获**：彻底理解 PBR 材质，为 Lv3 模型加载打好材质基础

### 2.9 🎯 综合项目：3D 房间漫游（2小时）
**Demo**: `project-02-room-tour.html`
- 几何体搭建房间 + 光影阴影 + 第一人称漫游（WASD）+ 粒子灰尘
- **收获**：完整3D场景搭建能力

---

## Lv3 — 模型加载与交互（10-14天）

> **目标**：加载外部模型，实现交互，做出"像产品"的3D页面
> **难度**：★★★☆☆

### 3.1 GLTF/GLB 模型加载（1小时）
**Demo**: `demo-14-load-model.html`
- 加载 GLB 模型、调整大小位置、加载进度、失败处理
- 免费模型资源：[Sketchfab](https://sketchfab.com/)、[Khronos glTF Samples](https://github.com/KhronosGroup/glTF-Sample-Models)
- **收获**：引入外部3D资源

### 3.2 模型动画播放（1.5小时）
**Demo**: `demo-15-model-animation.html`
- 骨骼动画播放、多动画切换、淡入淡出混合
- AnimationMixer / AnimationClip / AnimationAction
- **收获**：让模型动起来

### 3.3 纹理系统深入（1小时）⭐ 新增
**Demo**: `demo-16-texture-system.html`
- 颜色贴图、法线贴图、粗糙度贴图、金属贴图、AO贴图、环境贴图
- 贴图偏移 offset、重复 repeat、翻转 flipY
- 贴图加载管理器 TextureLoader + LoadingManager
- **收获**：掌握完整的纹理工作流

### 3.4 鼠标拾取与交互（1小时）
**Demo**: `demo-17-raycaster.html`
- Raycaster 射线检测、悬浮高亮、点击选中、弹出信息
- **收获**：3D场景核心交互能力

### 3.5 天空盒与环境（30分钟）
**Demo**: `demo-18-skybox.html`
- 天空盒（全景环境）、雾化效果、背景渐变
- **收获**：营造场景氛围

### 3.6 场景管理与 2D 标注（1小时）⭐ 整合
**Demo**: `demo-19-scene-management.html`
- Group 分组、显示/隐藏、场景切换、克隆
- Sprite 精灵标注（始终面向屏幕）
- CSS2DRenderer 标签（HTML 内容标注）
- **收获**：管理复杂场景 + 3D 场景中的信息展示

### 3.7 Shader 初体验：用 UV 做渐变（1小时）⭐ 新增 — Lv4 桥梁
**Demo**: `demo-20-shader-preview.html`
- 用 ShaderMaterial 替换 MeshBasicMaterial（回顾 Lv2 的 UV 理解）
- 片元着色器最简单的 UV 渐变：`gl_FragColor = vec4(vUv.x, vUv.y, 0.0, 1.0);`
- 不深入 GLSL，只感受"替换材质"的魔法
- **收获**：**为 Lv4 Shader 学习做最后铺垫，消除"突然写GLSL"的恐惧**

### 3.8 🎯 综合项目：3D 产品展示官网（3小时）
**Demo**: `project-03-product-page.html`
- GLB模型 + PBR材质 + 纹理贴图 + 颜色切换 + 动画 + 响应式
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
| [古柳·着色器基础（专栏）](https://juejin.cn/column/7095538674886344717) | 专栏 | attribute/uniform/varying、纹理采样、噪声（4篇） |
| [The Book of Shaders](https://thebookofshaders.com/) | 交互书 | GLSL 圣经，从形状到噪声到分形 |
| [Shadertoy](https://www.shadertoy.com/) | 平台 | 海量 Shader 源码，模仿学习 |
| [Inigo Quilez](https://iquilezles.org/) | 博客 | Ray Marching、SDF、噪声（进阶） |
| [阳轩·Three.js 进阶之旅](https://juejin.cn/column/7142349626215104526) | 掘金专栏 | Shader + 光源 + 粒子 + 性能 |
| [B站「进华」three.js教程](https://www.bilibili.com/video/BV1Gg411X7FY/) | 视频 | 从入门到入门，简洁清晰 |
| [犹他大学图形学课程](https://www.bilibili.com/video/BV1kf4y1N7vX) | 视频 | 2020秋，中英字幕，MVP 变换深入 |

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

## Lv5 — 工程化与商业项目落地（持续，4-6周）

> **目标**：从零到上线交付多个完整商业项目，构建有竞争力的作品集
> **难度**：★★★★★
> **核心理念**：Lv5 不是"一个毕业项目"，而是**多个可上线项目组成的作品集**

### 💼 为什么需要多个落地项目？

| 项目数量 | 面试效果 |
|----------|---------|
| 1 个项目 | "你会做3D" — 及格 |
| 3 个项目 | "你有经验" — 良好 |
| 5+ 个项目 | "你是专家" — 优秀，薪资谈判有底气 |

---

### 🏗️ 工程化基础（先学，1周）

### 5.0.1 工程化搭建（2小时）
**Demo**: `demo-30-engineering-setup.html`
- Vite + TypeScript 项目模板
- 目录结构设计（scene/camera/resources/events 单例模式）
- ESLint + Prettier + Husky
- 环境变量配置（dev/staging/prod）
- **收获**：专业级项目骨架

### 5.0.2 资源管理（1.5小时）
**Demo**: `demo-31-resource-management.html`
- 预加载队列 + 加载进度条
- 异常兜底（模型加载失败、贴图404）
- 资源缓存策略
- **收获**：用户不会看到白屏

### 5.0.3 前端框架集成（2小时）
**Demo**: `demo-32-framework-integration.html`
- React + react-three-fiber 入门
- 或 Vue3 + TresJS 入门
- 3D 场景组件化封装
- **收获**：3D 融入现代前端技术栈

### 5.0.4 移动端适配（1.5小时）
**Demo**: `demo-33-mobile-adapt.html`
- 触摸手势（单指旋转/双指缩放/双指平移）
- 设备性能检测（低/中/高配自动降级）
- 响应式布局
- **收获**：手机端流畅运行

### 5.0.5 打包部署（1.5小时）
**Demo**: `demo-34-deploy.html`
- Vite 打包配置
- 静态资源 CDN 配置
- 解决打包后资源 404
- Vercel/Netlify 一键部署
- **收获**：项目可访问线上 URL

---

### 🎯 落地项目（5 个，每个 2-5 天）

### 🏆 项目 1：3D 数字孪生园区系统（3-5天）⭐ 高薪方向
**Demo**: `project-05-digital-twin.html`

| 模块 | 内容 | 技能点 |
|------|------|--------|
| 场景搭建 | 建筑模型加载、道路、绿化、园区布局 | GLB 加载、场景管理 |
| 数据对接 | 后端 API 数据点位（设备状态、告警信息） | fetch/WebSocket、数据绑定 |
| 交互系统 | 点击建筑 → 弹窗详情、设备高亮、告警闪烁 | Raycaster、事件系统 |
| 视角控制 | 预设视角切换、双击聚焦、自动漫游 | 相机动画、Tween |
| 性能优化 | LOD 分级加载、视锥剔除、贴图压缩 | 大场景优化 |
| 部署上线 | CDN 部署、线上可访问 | 打包部署 |

**面试展示**：园区 3D 可视化 + 实时数据 + 交互操作 + 流畅性能

### 🏆 项目 2：3D 互动产品官网（2-3天）
**Demo**: `project-06-product-landing.html`

| 模块 | 内容 | 技能点 |
|------|------|--------|
| 产品展示 | 产品 GLB 模型 360° 展示 | 模型加载、环境贴图 |
| 材质切换 | 颜色/材质实时切换（如汽车选色） | PBR 材质、动态更新 |
| 动画效果 | 产品旋转展示、爆炸动画、部件高亮 | 动画系统 |
| 页面布局 | 3D 画布 + HTML 信息面板混合布局 | CSS + 3D 结合 |
| 移动端 | 触摸交互、响应式、性能降级 | 移动端适配 |

**面试展示**：产品官网级别的 3D 展示 + 材质切换 + 移动端可用

### 🏆 项目 3：3D 数据可视化大屏（3-4天）⭐ 高频需求
**Demo**: `project-07-data-dashboard.html`

| 模块 | 内容 | 技能点 |
|------|------|--------|
| 3D 地图底图 | 中国地图/城市地图 3D  extrusion | GeoJSON 解析、ExtrudeGeometry |
| 数据柱状图 | 3D 柱状图（BarChart）在地图上展示 | 动态几何体、数据映射 |
| 飞线效果 | 城市间数据流向飞线动画 | 贝塞尔曲线、Shader 动画 |
| 实时数据 | WebSocket 实时推送数据更新 | 数据绑定、动态更新 |
| 大屏适配 | 高分辨率适配、多屏联动 | 分辨率适配 |
| 交互面板 | 点击柱状图弹出详情、数据筛选 | Raycaster、UI 交互 |

**面试展示**：大屏级数据可视化 + 实时数据 + 3D 地图

### 🏆 项目 4：3D 虚拟展厅/看房（3-4天）
**Demo**: `project-08-virtual-showroom.html`

| 模块 | 内容 | 技能点 |
|------|------|--------|
| 展厅场景 | 室内场景搭建（墙壁/地板/灯光/展品） | 场景搭建、光照设计 |
| 第一人称漫游 | WASD 行走 + 鼠标环顾（PointerLockControls） | 第一人称控制 |
| 热点交互 | 走近展品 → 弹出介绍、点击查看详情 | 距离检测、UI 弹窗 |
| 小地图导航 | 右上角小地图、点击跳转 | 小地图、相机控制 |
| 场景切换 | 不同展厅/房间切换 | 场景管理 |
| 移动端 | 虚拟摇杆操控 | 移动端适配 |

**面试展示**：可漫游的虚拟展厅 + 热点交互 + 小地图

### 🏆 项目 5：3D 产品配置器（3-4天）⭐ 电商方向
**Demo**: `project-09-product-configurator.html`

| 模块 | 内容 | 技能点 |
|------|------|--------|
| 产品模型 | 加载产品基础模型（如汽车/沙发/手表） | GLB 加载 |
| 部件切换 | 轮毂/颜色/材质/配件实时切换 | 模型部件管理、材质动态更新 |
| 价格计算 | 选择配置 → 实时计算价格 | 业务逻辑 + UI |
| 截图导出 | 当前视角截图 → 下载/分享 | Canvas 导出 |
| 360° 旋转 | 自动旋转展示 + 手动拖拽 | OrbitControls |
| AR 预览 | WebXR 手机 AR 预览（可选） | WebXR |

**面试展示**：可交互的产品配置器 + 价格联动 + 截图导出

---

### 🏆 项目 6（可选）：3D 城市/交通可视化（3-5天）
**Demo**: `project-10-city-visualization.html`

| 模块 | 内容 | 技能点 |
|------|------|--------|
| 城市建筑 | 程序化生成建筑群（高度/颜色随机） | 程序化几何体 |
| 交通流线 | 道路 + 车辆移动动画 | 路径动画 |
| 昼夜切换 | 光照随时间变化（清晨→正午→黄昏→夜晚） | 光照动画、Shader |
| 天气效果 | 雨天/雪天/雾天切换 | 粒子系统、雾化 |
| 数据叠加 | 建筑上叠加数据标签（温度/人流） | CSS2D/Sprite 标注 |

**面试展示**：城市级 3D 可视化 + 程序化生成 + 环境切换

---

## 📊 总 Demo 数量统计

| 阶段 | 小 Demo | 综合项目 | 合计 | 说明 |
|------|---------|---------|------|------|
| Lv1 快速上手 | 5 | 1 | 6 | 全部 ✅ |
| Lv2 深入理解 | 8 | 1 | **9** | +PBR深入 |
| Lv3 模型交互 | 7 | 1 | **8** | +纹理系统+Sprite标注+Shader初体验 |
| Lv4 Shader+性能 | 12 | 1 | 13 | Shader 10专项+3性能+1项目 |
| Lv5 工程化+落地 | 5 | **6** | **11** | 工程化基础 + 6个落地项目 |
| **总计** | **37** | **10** | **47** | |

---

## 🎯 项目作品集建议

面试时选择 **3 个最有代表性的项目** 展示：

| 组合 | 展示方向 | 目标岗位 |
|------|---------|---------|
| 数字孪生 + 数据大屏 + 城市可视化 | 数字孪生/智慧城市 | 政企大厂（20k-40k） |
| 产品官网 + 配置器 + 虚拟展厅 | 电商/品牌展示 | 互联网公司（15k-30k） |
| 全部 6 个 | 全能型 3D 前端 | 高级/专家（30k-50k+） |

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
| Day 10-11 | Lv2.7 阴影 + Lv2.8 PBR深入 | ☐ |
| Day 12 | Lv2.9 🎯 3D房间漫游 | ☐ |
| Day 13-15 | Lv3.1 模型加载 + Lv3.2 动画 + Lv3.3 纹理系统 | ☐ |
| Day 16-18 | Lv3.4 鼠标拾取 + Lv3.5 天空盒 + Lv3.6 场景管理 | ☐ |
| Day 19 | Lv3.7 Shader初体验 + Lv3.8 🎯 产品展示官网 | ☐ |
| Day 20-22 | Lv4.1 第一个ShaderMaterial + Lv4.2 GLSL速成 + Lv4.3 数据传递 | ☐ |
| Day 23-26 | Lv4.4 顶点着色器 + Lv4.5 片元UV创意 + Lv4.6 纹理采样 | ☐ |
| Day 27-30 | Lv4.7 噪声算法 + Lv4.8 经典特效 | ☐ |
| Day 31-33 | Lv4.9 后处理 + Lv4.10 🎯 Shader特效秀 | ☐ |
| Day 34-37 | Lv4.11 性能优化 + Lv4.12 资源优化 + Lv4.13 物理引擎 | ☐ |
| Day 38-40 | Lv5 工程化基础（搭建/资源/框架/移动端/部署） | ☐ |
| Week 7-8 | 🏆 项目1: 数字孪生园区 | ☐ |
| Week 8-9 | 🏆 项目2: 3D产品官网 + 🏆 项目3: 数据大屏 | ☐ |
| Week 9-10 | 🏆 项目4: 虚拟展厅 + 🏆 项目5: 产品配置器 | ☐ |
| Week 10-11 | 🏆 项目6: 城市可视化（可选） | ☐ |

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