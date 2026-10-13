# embedded-effort-estimation
根据框图、规格书、PPT 等项目资料，执行通用流程：

**读资料 → 拆分工作项 → 标注型号和数量 → 编写 Note → 检查遗漏与重复。**

## 能力

- 按实际范围拆分环境、基线、Bring-up、外设、MCU、测试及认证工作。
- 标注已确认的器件型号和数量，区分未知信息与新增建议。
- 用简短 Note 描述工作与完成目标，用 Comments 记录依赖和前提。
- 检查遗漏与重复，形成可供人力评估的工作项表；人力和报价留空。

## 使用

将仓库作为 `embedded-effort-estimation` 技能目录加载，在支持 Skill 的工具中调用：

```text
使用 $embedded-effort-estimation 根据附件拆分评估工作项，
给出简短 Note，型号和数量标清，人力先留空。
```

## 内容

- [SKILL.md](SKILL.md)：拆分流程与范围规则。
- [table-rules.md](references/table-rules.md)：字段定义、Note 示例和项目拆分粒度。
- [review-cases.md](references/review-cases.md)：拆分检查场景，非已执行测试报告。
- [evaluation-template.csv](assets/evaluation-template.csv)：八列表头模板。
- [openai.yaml](agents/openai.yaml)：技能展示信息。

## License

[Apache License 2.0](LICENSE)
