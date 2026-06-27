# TableNorm — 表格列名标准化

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Version](https://img.shields.io/badge/version-1.2.1-brightgreen)](https://github.com/kaXianc2-gom/table-norm/releases)
[![Pages](https://img.shields.io/badge/demo-online-0078D4)](https://kaXianc2-gom.github.io/table-norm/)

> 各省职位表列名五花八门——"招录机关"、"用人单位"、"招考单位"——自动映射到 16 个标准字段，一键导出。

单文件 HTML，双击即用。拖入 Excel 自动检测列名、显示匹配结果、人工微调、导出标准化文件。

## 解决了什么问题

国考加 31 省省考，每年的职位表列名都不统一。同样的"部门名称"，可能出现：招录机关、用人单位、招录单位、单位名称、用人司局、招考单位、录用单位、招聘单位、机关名称、所属部门、主管单位……

如果你需要合并多省数据做筛选，第一步永远是手工对列表头。TableNorm 把这个过程自动化了。

## 怎么用

1. 下载 index.html，双击打开
2. 拖入职位表（支持 .xlsx / .xls / .csv，多文件批量合并）
3. 自动检测每列对应的标准字段，绿/黄/红三色标记置信度
4. 手动调整不满意的映射（下拉选择器）
5. 点"应用标准化" → 预览 → 导出 Excel 或 CSV

导出的文件可以直接喂给 SheetLens 做筛选。

## 匹配原理

不是 AI，是规则匹配：

- **精确匹配**：列名完全相同 → 置信度 100%
- **包含匹配**：列名包含同义词 → 置信度 90%
- **模糊匹配**：Jaccard 字符相似度 + 最长公共子串 → 50-89%

16 个标准字段，每个 5-15 个同义词，共 100+ 变体。CSV 自动检测 UTF-8 / GBK 编码，自动跳过合并单元格标题行。

## 16 个标准字段

| 字段 | 说明 |
|------|------|
| department | 部门名称 |
| title | 职位名称 |
| level | 机构层级 |
| attr | 职位属性 |
| examType | 考试类别 |
| count | 招考人数 |
| major | 专业要求 |
| education | 学历要求 |
| degree | 学位要求 |
| party | 政治面貌 |
| experience | 基层工作年限 |
| otherReq | 其他条件 |
| province | 省份 |
| location | 工作地点 |
| interviewRatio | 面试比例 |
| notes | 备注 |

## 🌐 在线体验

无需下载，直接使用：**[🔗 在线 Demo](https://kaXianc2-gom.github.io/table-norm/)**

## 🔐 隐私声明

- **数据不上传**：所有列名检测、标准化处理均在浏览器本地内存中完成
- **无网络请求**：SheetJS 已内联，运行时零外部请求
- **无持久化存储**：关闭浏览器后数据自动清除

> ⚠️ **免责声明**：本工具仅供数据整理与参考辅助。标准化结果请以原始文件为准。

## 技术

纯 HTML + JS，SheetJS 内联（离线可用），单文件约 920KB。数据全部浏览器本地处理。

## 生态位置

TableNorm → DataVeil → SheetLens → PostCmp → AppTrack

## 测试

打开 `index.html?test=1`，控制台输出 14 个匹配引擎测试结果。

MIT License
