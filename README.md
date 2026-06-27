# 🧹 TableNorm — 表格列名标准化器

[![License](https://img.shields.io/badge/license-MIT-blue)](LICENSE)
[![Version](https://img.shields.io/badge/version-v1.0.0-green)](https://github.com/kaXianc2-gom/table-norm/releases)

> 各省公考职位表列名五花八门——"招录机关"、"用人单位"、"招考单位"——TableNorm 自动检测并映射到 16 个标准字段，一键导出统一格式。

## 🎯 解决的痛点

国考 + 31 省省考职位表的列名各不相同：

| 标准字段 | 实际可能出现的列名 |
|----------|-------------------|
| 部门名称 | 招录机关、用人单位、招录单位、单位名称、用人司局、招考单位、录用单位… |
| 职位名称 | 招考职位、招录职位、岗位名称、招聘岗位、拟任职位… |
| 招考人数 | 招录人数、计划招录、招录计划、招聘数量、招录名额… |
| 专业要求 | 专业、学科、所学专业、专业名称、报考专业、学科门类… |

人工对列表头 → 复制粘贴 → 改列名 → 合并，太痛苦。TableNorm 把这个过程自动化。

## ✨ 功能

### 📤 上传解析
- 支持 `.xlsx` / `.xls` / `.csv` 三种格式
- 多文件批量上传，自动合并
- CSV 自动检测 UTF-8 / GBK 编码
- 自动跳过说明行（合并单元格标题等）
- 文件大小限制 30MB

### 🔍 智能列名检测
- **同义词字典**：16 个标准字段，每个 5-15 个同义词，共 100+ 列名变体
- **三级匹配策略**：
  - 精确匹配（100%）— "部门名称" = `department`
  - 包含匹配（90%）— "招录机关" ≈ `department`
  - Jaccard 相似度 + 最长公共子串（50-89%）— 字符级计算
- 绿色/黄色/红色三色标记置信度

### ✏️ 人工修正
- 每列下拉选择器手动调整映射
- 支持"跳过/未知"标记
- 一键"🪄 自动匹配"重新检测

### 📋 标准化预览
- 前 100 行数据实时预览
- 仅显示有数据的有效列
- 统计总行数 + 映射字段数

### 📥 导出
- 标准 Excel（`.xlsx`）— 直接导入 SheetLens
- CSV（UTF-8 BOM）— Excel 打开不乱码

## 🚀 快速开始

1. [下载 index.html](https://github.com/kaXianc2-gom/table-norm/releases/latest)
2. 双击打开（纯 HTML，零安装）
3. 拖拽或点击上传职位表
4. 确认列名映射 → 点「✅ 应用标准化」
5. 导出 Excel → 导入 SheetLens 继续筛选

## 🔧 技术架构

| 项目 | 说明 |
|------|------|
| 语言 | 纯 HTML + CSS + JavaScript (ES5) |
| 依赖 | SheetJS（CDN 加载） |
| 架构 | 单文件，零构建，零后端 |
| 隐私 | 浏览器本地处理，数据不上传 |
| 大小 | ~44 KB（不含 SheetJS） |

## 🏛 在生态中的位置

```
TableNorm → DataVeil → SheetLens → PostCmp → AppTrack
 (清洗)      (脱敏)      (筛选)      (对比)     (追踪)
```

🌐 启动器：[GWY LaunchPad](https://github.com/kaXianc2-gom/gwy-launchpad)

## 📱 设备支持

| 桌面 | 平板 | 手机 |
|------|------|------|
| ✅ 完整 | ✅ 可用 | ⚠ 映射表需横向滚动 |

## 🧪 测试

打开 `index.html?test=1`，控制台运行 14 个测试用例。

## 🤖 AI 辅助

本项目使用 Claude（Anthropic Claude Code）辅助开发，所有代码经人工审查。

## 📄 许可证

MIT License
