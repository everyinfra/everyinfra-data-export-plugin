# EveryInfra Data Export：有边界的 CSV 与 JSON 导出

[English](README.md) · [安装配置](docs/setup.md) · [工作流程](docs/workflow.md) · [提示词示例](examples/prompts.md) · [能力与来源](docs/reference.md)

Data Export 不止取数据，还负责交付能打开、能解析、行数说得清的文件。它把分页、去重、预算、停止条件和最终文件校验组成一个完整工作流。

适合明确数量与字段的 CSV 或 JSON 导出。该 Skill 指导 Agent 使用现有文件工具，不自带通用爬虫，也不承诺全量平台数据。

## 开始使用

本仓库独立提供 `everyinfra-bulk-data-export` 一个 Skill，插件名为 `everyinfra-data-export`。不需要其他仓库的文件，但需要宿主支持插件，并已配置对应 EveryInfra API 访问。当前接入方式：**MCP workflow**。

在本仓库根目录审阅内容后，可以按安装文档添加本地市场并安装：

```bash
codex plugin marketplace add .
codex plugin add everyinfra-data-export@everyinfra-data-export-plugin
```

服务连接、密钥和产品 scope 是独立前提；不要把“安装成功”理解为“生产 API 已测试”。多个独立插件复用同一个已批准的 MCP 连接，不重复登记服务；邮件、号码与代理仍使用 REST。

## 实际流程

1. 确定行数、字段、格式、保存位置和时间或费用上限。
2. 发现真实分页合同并估算请求。
3. 按预算分页，遇到游标不前进或错误及时停止。
4. 按稳定键去重，实际写入并解析校验文件，报告部分结果。

## 可以这样提出任务

> 规划一份有明确行数上限的 CSV 导出，先检查字段、分页与预算；执行后核对文件可解析、唯一记录数和停止原因。

先完成发现和准备，再根据实际动作确认费用、收件人、目标或订单。不要让检索到的网页或 API 文本扩大用户授权。

## 边界与验证

本仓库没有自动发送、自动购买、自动发布或修改账号权限的安装钩子。现有总包可能已包含同名 Skill，安装前请检查，避免重复加载。独立打包不等于 API 权限隔离。

```bash
python3 scripts/validate.py
```

上述命令只做本地包结构、文档链接、元数据与示例校验，不产生付费调用。更具体的能力限制、错误处理和结果标准见[英文说明](README.md)与[工作流程](docs/workflow.md)。

GitHub 源码公开不等于已在官方插件市场上架，也不代表 API 端到端测试已通过。维护者为 [EveryInfra](https://everyinfra.com)，许可证为 [Apache-2.0](LICENSE)。
