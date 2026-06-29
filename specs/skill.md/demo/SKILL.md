---
name: pdf-editor
description: Edits PDF files including filling forms, extracting text, and merging documents. Use when the user wants to modify a PDF.
---

# PDF Editor

本 skill 让 Claude 能直接操作 PDF 文件——填表、抽取文本、合并文档、添加水印。

## 何时触发

- 用户上传一份 PDF 并要求填表、签字、合并、拆分、转换
- 用户提问涉及"修改 PDF 的某些内容"
- 工作流中需要把 PDF 表单字段填入数据

## 使用

读完本文件后:

- **填表流程**:跳到 [forms.md](forms.md),里面有字段定位、值写入、扁平化的完整步骤
- **API 参考**:[reference.md](reference.md) 列出 `pypdf` 和 `pdfplumber` 在本 skill 里的封装函数
- **执行脚本**:`scripts/fill_form.py`、`scripts/merge.py`,直接 `python scripts/<name>.py --help` 查用法

## 注意

- 处理大文件(> 50MB)时先看 `reference.md` 的「内存策略」一节
- 涉及法律/合同类 PDF 修改后必须保留原文件备份,新文件加 `-edited` 后缀
- 表单字段名因 PDF 生成器而异,详见 `forms.md` 的命名指南
