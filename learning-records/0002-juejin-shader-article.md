# 0002 — 掘金 Shader 文章参考与学习计划 v3 更新

参考了掘金·古柳的「Three.js Shader 入门教程（一）」([链接](https://juejin.cn/post/7233359844974182437))，
将其核心方法论整合到学习计划中。

**关键收获**：
- Shader 学习应该从"理解几何体内部数据"开始，而非直接写 GLSL
- 路径：几何体顶点 → vertex attributes(position/uv/normal) → UV可视化 → ShaderMaterial替换 → GLSL语法 → 片元着色器
- 这比直接跳入 WebGL 原生渲染管线平缓得多

**对学习计划的改变**：
- Lv2 新增 2.1「几何体内部结构」和 2.2「UV 纹理坐标」作为 Shader 铺垫
- Lv4 Shader 部分完全重构，采用渐进路径：复习顶点属性 → 第一个ShaderMaterial → GLSL速成 → 顶点着色器MVP → 片元UV创意 → 高级特效
- 新增资源：B站进华、犹他大学图形学课程、知乎 MVP 文章、Codepen 示例

**Implications**：
- 从 Lv2 到 Lv4 的过渡更平滑，不再有"Three.js API → 突然写GLSL"的断层
- 学习计划从 v2 升级到 v3，总 Demo 数从 33 增至 35