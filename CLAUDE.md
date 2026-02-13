# Reading Note Repository - Claude Code Guidelines

## 项目概述

这是一个研究论文阅读笔记仓库，用于记录和整理 AI/ML 领域的研究论文摘要和笔记。

## 主要分类

| 分类 | 描述 |
|------|------|
| **Inference** | 推理优化、KV Cache、注意力机制优化 |
| **Agent** | 智能体、多智能体系统、工具调用 |
| **CoT** | 思维链、推理效率、测试时扩展 |
| **Long-Context** | 长上下文处理、记忆机制 |
| **RAG** | 检索增强生成 |
| **Evaluation** | 评估基准、测试方法 |

## 已知 Bug 和问题

### Markdown 表格渲染问题

**问题描述：** GitHub Markdown 要求每个表格必须有表头行，否则无法正确渲染。

**解决方案：** 每个子表必须包含表头：
```markdown
| 📖 Reading Note | 📅 Date | 🏷️ Keywords | 🔗 Link |
|:---------------|:-------:|:-----------:|:-------:|
```

**历史修复记录：**
- `ddd7236`: 修复 More Papers (2025) 表头
- `150e24a`: 添加所有子表表头
- `2345f5b`: 添加空行分隔表格
- `362a8ae`: 修复表头对齐

### 文件命名规范

- 使用下划线 `_` 连接单词
- 避免使用空格和特殊字符
- 例如：`Beyond_Task_Level_Isolation.md`

## 偏好设置

### 论文分类规则

1. **Inference** - KV Cache 优化、推理加速、注意力机制
2. **Agent** - 多智能体、工具调用、工作流
3. **CoT** - 思维链、推理效率、测试时扩展
4. **Long-Context** - 长上下文、记忆
5. **RAG** - 检索增强
6. **Evaluation** - 基准测试、评估

### README 更新流程

1. 添加新论文到对应分类
2. 确保表格包含完整表头
3. 格式：`| 标题 | 日期 | 关键词 | [链接] |`

### Commit 信息格式

```
feat: add X new research papers
fix: correct table header alignment
docs: update CLAUDE.md
```

## 统计

- 总论文数：130+
- 主要分类：Inference (39), CoT (29), Agent (20)

## 注意事项

1. 新增论文时检查是否已存在
2. 表格必须有表头行
3. 文件路径使用相对路径 `./Category/filename.md`
4. 日期格式：`YYYY-MM-DD`

