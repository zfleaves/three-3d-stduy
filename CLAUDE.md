# Three.js 3D 学习项目 — 课件生成规范

> 本文件为项目级 CLAUDE.md，遵循全局 `C:\Users\admin\.claude\CLAUDE.md` 中的教学规范。
> 生成任何课件前，必须先 invoke `/teach` skill。

## 项目特定规则

### 学习计划来源
- `docs/base.md`：五级系统化学习大纲（Lv1-Lv5），包含知识点、常见错误、通关标准
- `STUDY-PLAN.md`：整合 base.md + BOSS直聘招聘要求的学习计划
- 招聘市场对标：数字孪生、智慧城市、3D产品展示、数据可视化大屏

### 五级递进结构
```
Lv1 快速上手（3天）    → Three.js 基础API，先建立信心
Lv2 深入理解（5-7天）  → 坐标/纹理/动画/粒子/阴影
Lv3 模型交互（7-10天） → GLB加载/PBR材质/射线拾取/动画
Lv4 底层优化（10-15天）→ WebGL/Shader/后处理/性能/物理
Lv5 商业项目（持续）   → 工程化/部署/数字孪生毕业项目
```

### 课件命名
- `lessons/demo-NN-slug.html` — 小 Demo（NN 从 01 递增）
- `lessons/project-NN-slug.html` — 综合项目
- 编号全项目统一，不按等级重置

### 每个 Demo 的技术要求
- 使用 Three.js CDN import map（版本 0.160.0）
- 所有 Demo 必须有 OrbitControls（除了第一个入门 Demo）
- 使用 MeshStandardMaterial（PBR）作为默认材质
- 渲染器开启 antialias 和 shadowMap
- 包含 ResizeObserver 响应式适配
- 代码中关键步骤用注释标注

### 已完成的课件
- [x] Lv1 Demo 01: Hello Cube
- [x] Lv1 Demo 02: 几何体家族
- [x] Lv1 Demo 03: 光影魔法
- [x] Lv1 Demo 04: 鼠标控制视角
- [x] Lv1 Demo 05: 材质初探
- [x] Lv1 Project 01: 3D产品展示台

### 下一步待生成
- [ ] Lv2 Demo 06-12 + Project 02
- [ ] Lv3 Demo 13-18 + Project 03
- [ ] Lv4 Demo 19-26 + Project 04
- [ ] Lv5 工程化 + 毕业项目
- [ ] reference/ 速查参考（GLOSSARY.md 术语表、API速查等）