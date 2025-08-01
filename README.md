<!-- Project Banner -->

<p align="center">
  <img src="docs/banner_mechonfluid.png" width="600" alt="MechOn – Mechanics Ontology" />
</p>

# MechOn‑fluid

> **Mechanics Ontology for Fluid Dynamics**
> OWL DL 本体  • 可视化工具  • 实践教程

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Build](https://github.com/cocoJ-P/MechOn-fluid/actions/workflows/ci.yml/badge.svg)](…)
[![DOI](https://zenodo.org/badge/…)](…)
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/cocoJ-P/MechOn-fluid/HEAD?urlpath=%2Fdoc%2Ftree%2FUserGuide%2FMechOnshowcase-zh.ipynb)

---

## ✨ 项目目录总览

<p align="center">
  <img src="docs/MechOn-fluid-flowchart.png" width="900" alt="Repository structure of MechOn‑fluid" />
</p>

### 流程图说明

**Ontology 模块（左侧）**

| 文件                   | 说明                                         | 作用层级 |
| ---------------------- | -------------------------------------------- | -------- |
| **`mechon-fluid.owl`** | 主入口；仅包含 `owl:imports`、前缀与元数据   | 根本体   |
| **`mat.core.ttl`**     | 数学层：张量 / 场 / 对称性等                 | TBox     |
| **`geo.core.ttl`**     | 几何层：坐标系 / 计算域 / 边界等             | TBox     |
| **`phy.core.ttl`**     | 物理量层：密度、压力、雷诺数…                | TBox     |
| **`qk-alignment.ttl`** | `phy:` ↔ **QUDT** (`qudt:QuantityKind`) 对齐 | 映射桥   |

**Rules 模块（右侧）**

| 文件                         | 作用                                                            |
| ---------------------------- | --------------------------------------------------------------- |
| **`derivedQuantities.swrl`** | DL‑Safe SWRL 规则：如自动识别 Rank‑0  张量 → `mat:ScalarTensor` |
| **`validationTest.sparql`**  | SPARQL 断言脚本：质控缺失属性 / 约束冲突                        |

---

## 🗂️ 关键组件与示例

| 组件            | 说明                                             | 路径                                   |
| --------------- | ------------------------------------------------ | -------------------------------------- |
| **核心  TBox**  | `mat.core.ttl` / `geo.core.ttl` / `phy.core.ttl` | `ontology/`                            |
| **QUDT 对齐桥** | 量纲、单位自动继承                               | `ontology/qk-alignment.ttl`            |
| **规则库**      | Rank  自动归类、派生量注入                       | `rules/derivedQuantities.swrl`         |
| **质控脚本**    | SPARQL 检查缺失属性、约束冲突                    | `rules/validationTest.sparql`          |
| **上手教程**    | TTL → Protégé → HermiT → PyVis                   | `notebooks/MechOnFluid_tutorial.ipynb` |

---

## 🚀 快速开始

### 1 · 克隆仓库 & 初始化

```bash
git clone https://github.com/cocoJ-P/MechOn-fluid.git
cd MechOn-fluid
```

### 2 · 在  Protégé 加载本体

1. 打开 `MechOn-Fluid/ontology/mechon-fluid.owl`（自动加载三棵子树）
2. 依次选择 _Reasoner → HermiT → Start_，确保无不一致
3. 按需编辑或扩展张量、坐标系、物理量

### 3 · 运行示例推理 & 可视化

```bash
conda env create -f environment.yml   # 安装依赖
jupyter lab notebooks/MechOnFluid_tutorial.ipynb
```

教程内容：

1. 使用 OWL‑API 载入本体
2. 调用 HermiT + SWRL 规则推理
3. 用 PyVis 绘制交互式知识图谱

---

## 📦 版本发布

| 版本       | 里程碑                          | 下载                                                                    |
| ---------- | ------------------------------- | ----------------------------------------------------------------------- |
| **v0.1.0** | 完成三棵核心  TBox + 首批张量族 | [Releases](https://github.com/cocoJ-P/MechOn-fluid/releases/tag/v0.1.0) |

---

## 📝 引用

```bibtex
@misc{mechon-fluid2025,
  title        = {MechOn-fluid: An OWL DL Ontology for Fluid Mechanics},
  author       = {Pang, Jiashun and An, Yi},
  year         = {2025},
  howpublished = {\url{https://github.com/cocoJ-P/MechOn-fluid}}
}
```

---

### 🤝 预告

本期 v0.1.0 将使用传统建模方式探索流体力学学科建模结构，mat\phy\geo 复合推理，建模最佳实践，将理论知识工程化
下期 v0.2.0 将探索 Infer+类建模模式，并拓展到实例建模
v1.0.0 将是正式批量大版本

---

<p align="center"><i>Building a sharable, extensible semantic backbone for fluid‑mechanics research.</i></p>
