# 学习计划审计报告

> 对照 CLAUDE.md 课件生成规范 + teach skill 要求，逐项检查 STUDY-PLAN.md

---

## ❌ 严重问题

### 1. `reference/` 目录和 GLOSSARY.md 完全缺失
teach skill 明确要求：「Glossaries, in particular, are an essential reference. Once one is created, it should be adhered to in every lesson.」
**影响**：所有课件缺少统一的术语定义，学员可能在不同 Demo 中看到同一概念的不同表述。

### 2. Lv3 内容严重不足（5 个 Demo 承载不了 base.md 的要求）
| base.md Lv3 要求 | 当前计划 | 状态 |
|---|---|---|
| 材质全体系（PBR/漫反射/高光） | 无独立 Demo | ❌ 缺失 |
| 纹理系统（颜色/法线/粗糙度/金属/环境贴图） | 无独立 Demo | ❌ 缺失 |
| 骨骼动画 | 3.2 一个 Demo | ⚠️ 不够 |
| Sprite 2D 标签 | 无 | ❌ 缺失 |
| 环境贴图对 PBR 的影响 | 无 | ❌ 缺失 |

---

## ⚠️ 中等问题

### 3. Lv2→Lv3→Lv4 存在断层
```
Lv2 铺垫了 Shader（几何体内部结构+UV）→ Lv3 完全跳到模型加载（铺垫白费）
→ Lv4 又重新拾起 Shader（需要回忆 Lv2 的内容）
```
**建议**：Lv3 末尾加一个 "Shader 初体验" demo，保持 Shader 学习连续性。

### 4. Lv3 缺少"响应式适配"基础
Lv5 才有移动端适配，但 Lv3 做产品页面时就应该接触。实际开发中，产品页面通常需要响应式。

### 5. Lv2 的 PBR 材质深度不够
Lv1.5 只介绍了 roughness/metalness 两个参数。Lv2 应该有一个 demo 深入 PBR：环境贴图如何影响金属反射、粗糙度如何影响漫反射。

### 6. 参考资源链接不全
- 知乎 MVP 文章只有标题，没有链接
- 缺少 Lv3 模型资源的下载链接（免费的 GLB 模型去哪找？）

---

## 🔧 小问题

### 7. Lv5 工程化 Demo（30-34）不适合做成 HTML 课件
这些是配置类内容（Vite配置、Webpack配置、部署脚本），更适合做成 `.md` 教程文档或视频。

### 8. Demo 时间估算需要校准
- Lv4.7 噪声算法标 2 小时，但噪声是 Shader 最难的部分，可能需要 3-4 小时
- Lv3.2 骨骼动画标 1 小时，但动画切换/混合/过渡需要更多时间

### 9. 缺少"在哪里找免费模型"的指引
Lv3 需要加载 GLB 模型，但学员不知道去哪里找免费的、带骨骼动画的 GLB 模型。应该提供资源链接。

---

## ✅ 做得好的地方

- Lv1 设计优秀，5+1 结构合理，6 个课件全部完成
- Shader 学习路径（几何体→UV→ShaderMaterial→GLSL）非常平缓
- Lv4 Shader 专项内容丰富，13 个 Demo 覆盖全面
- Lv5 6 个落地项目方向明确，与招聘市场对齐
- 资源汇总完整，链接可用
- 薪资对标清晰，学习动力强

---

## 📋 修复优先级

| 优先级 | 问题 | 修复方案 |
|--------|------|---------|
| P0 | GLOSSARY.md 缺失 | 创建术语表 |
| P0 | reference/ 缺失 | 创建 API 速查 HTML |
| P1 | Lv3 内容不足 | 增加 3 个 Demo：PBR深入、纹理系统、Sprite标签 |
| P1 | Lv3 末尾加 Shader 初体验 | 新增 demo-18 作为 Lv4 的桥梁（调整后续编号） |
| P2 | Lv2 增加 PBR 深入 | 新增 demo-13 或替换现有内容 |
| P2 | 补全资源链接 | 知乎 MVP 文章、免费模型下载站 |
| P3 | Lv5 工程化 Demo 改为教程文档 | 重命名 demo-30~34 → tutorial-01~05 |