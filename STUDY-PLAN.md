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

## Lv4 — Shader 着色器 + 性能优化（12-18天）⭐ 核心重构

> **目标**：从"理解几何体数据"平滑过渡到"写自定义 Shader"，彻底掌握底层
> **参考**：掘金·古柳「Three.js Shader 入门」系列 + 《The Book of Shaders》
> **难度**：★★★★☆

### 🔑 Lv4 Shader 学习路径（掘金文章方法论）

```
Lv2已铺垫(几何体内部结构+UV) → 复习顶点属性 → 替换ShaderMaterial
→ GLSL语法速成 → 顶点着色器MVP变换 → 片元着色器UV创意
→ 高级特效 → 后处理
```

### 4.1 复习顶点属性 + 第一个 ShaderMaterial（1小时）⭐
**Demo**: `demo-18-first-shader.html`
- 回顾 Lv2.1 的 `geometry.attributes`（position、uv、normal）
- 用 `ShaderMaterial` 替换 `MeshBasicMaterial`
- 写最简单的红色片元着色器：`gl_FragColor = vec4(1.0, 0.0, 0.0, 1.0);`
- 顶点着色器最小结构：`gl_Position = projectionMatrix * modelViewMatrix * vec4(position, 1.0);`
- 理解 ShaderMaterial vs RawShaderMaterial 的区别
- **收获**：**从内置材质到自定义 Shader 的第一步，理解"替换"的魔法**

### 4.2 GLSL 语言速成（1小时）⭐
**Demo**: `demo-19-glsl-basics.html`
- 数据类型：float、int、bool、vec2、vec3、vec4
- 向量分量访问：`.x .y .z .w` 和 `.r .g .b .a`
- 向量运算：逐分量计算、灵活组合 `vec3(vec2(0.5), 1.0)`
- 颜色范围：0.0-1.0（超出会被截取）
- 函数定义：以返回值类型开头，参数需写明类型
- 语句必须分号结尾
- **收获**：掌握 GLSL 基本语法，能看懂和修改 Shader 代码

### 4.3 顶点着色器与 MVP 变换（1.5小时）⭐
**Demo**: `demo-20-vertex-shader.html`
- MVP 变换全流程：Model → View → Projection
- `modelMatrix`：模型本地坐标 → 世界坐标
- `viewMatrix`：基于相机位置变换
- `modelViewMatrix`：前两者合并（Three.js 内置）
- `projectionMatrix`：3D → 2D 屏幕投影
- 顶点扰动效果：`position.y += sin(position.x * 3.0) * 0.1;`
- **收获**：理解顶点着色器如何控制物体形状和位置

### 4.4 片元着色器 + UV 创意（1.5小时）⭐
**Demo**: `demo-21-fragment-shader.html`
- 将 UV 直接作为颜色输出：`gl_FragColor = vec4(vUv.x, vUv.y, 0.0, 1.0);`
- UV 渐变效果（R=u, G=v）
- 重复条纹：`step(0.5, fract(vUv.x * 5.0))`
- 圆形图案：`length(vUv - 0.5)` 计算到中心的距离
- 颜色混合：`mix(color1, color2, factor)`
- **收获**：用 UV 坐标创造丰富的图案效果

### 4.5 常用 Shader 特效（2小时）
**Demo**: `demo-22-shader-effects.html`
- 溶解效果（discard + noise）
- 波纹效果（sin + distance）
- 描边效果（fresnel）
- 霓虹发光（smoothstep + glow）
- **收获**：掌握 4 种常用 Shader 特效

### 4.6 后处理特效（1小时）
**Demo**: `demo-23-postprocessing.html`
- EffectComposer 管线
- 辉光（Bloom）、景深（DOF）、画面调色
- **收获**：提升画面品质

### 4.7 性能优化（1.5小时）
**Demo**: `demo-24-performance.html`
- 1000个立方体：普通 vs InstancedMesh
- FPS 监控、几何体合并、视锥剔除
- **收获**：让场景跑得流畅

### 4.8 贴图与资源优化（1小时）
**Demo**: `demo-25-texture-optimization.html`
- 贴图 2 的幂次方规范、纹理压缩
- 资源销毁（防止内存泄漏）
- SPA 路由切换时的资源清理
- **收获**：避免线上事故

### 4.9 物理引擎（1.5小时）
**Demo**: `demo-26-physics.html`
- Cannon-es 重力+碰撞+弹跳
- **收获**：场景有物理真实感

### 4.10 🎯 综合项目：Shader 特效秀（3小时）
**Demo**: `project-04-shader-show.html`
- 多个自定义 Shader 特效组合
- 辉光后处理 + 性能优化 + 鼠标交互
- **收获**：展示技术深度的作品

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
| Lv4 Shader+性能 | 9 | 1 | **10** | 重构：Shader 平缓渐进 |
| Lv5 工程化 | 4 | 1 | 5 | — |
| **总计** | **30** | **5** | **35** | |

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
| Day 20-21 | Lv4.1 第一个ShaderMaterial + Lv4.2 GLSL速成 | ☐ |
| Day 22-24 | Lv4.3 顶点着色器 + Lv4.4 片元着色器UV创意 | ☐ |
| Day 25-27 | Lv4.5 Shader特效 + Lv4.6 后处理 | ☐ |
| Day 28-30 | Lv4.7 性能优化 + Lv4.8 资源优化 | ☐ |
| Day 31-33 | Lv4.9 物理引擎 + Lv4.10 🎯 Shader特效秀 | ☐ |
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