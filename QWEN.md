# Qwen 工作流入口

这是安装到 Qwen extension 里的薄入口文件。

它负责三件事：

1. 给出统一任务开始方式
2. 说明固定 workflow 的选路规则
3. 指向 extension 内的 `commands/`、`skills/`、`agents/` 详细内容

## 核心规则

- 默认先评估任务类型，再选对应 workflow
- 中文优先，技术契约保持原样
- 证据先于断言，完成前必须验证
- 命令统一使用 `zc:` 命名空间，避免和平台内置能力冲突

## 固定 workflow

### 1. product-analysis
- 入口：`zc:product-analysis`
- 适用：需求模糊、价值与范围未收敛

### 2. full-delivery
- 入口：`zc:sdd-tdd`
- 适用：新功能、较大改动、完整交付

### 3. bugfix
- 入口：`zc:debug`
- 适用：Bug、失败测试、异常行为

### 4. review-closure
- 入口：`zc:quality-review`
- 适用：已有改动，需要审查与反馈收敛

### 5. docs-release
- 入口：`zc:doc` 或 `zc:ship`
- 适用：文档、ADR、发布说明、上线准备

### 6. investigation
- 入口：`zc:onboard` 或 `zc:ctx-health`
- 适用：陌生代码库、上下文失焦、技术摸底

## 推荐开始方式

- 不确定走哪条线：先用 `zc:start`
- 需求模糊：进 `zc:product-analysis`
- 已确认是完整交付：进 `zc:sdd-tdd`
- 明确是 bug：进 `zc:debug`

## 最常用入口速查

- 做新需求但范围还没收敛：`zc:product-analysis`
- 进入完整交付主流程：`zc:sdd-tdd`
- 修 bug：`zc:debug`
- 做代码审查和反馈收敛：`zc:quality-review`
- 补文档或发布说明：`zc:doc`
- 陌生项目先摸底：`zc:onboard` 或 `zc:ctx-health`

## 详细内容在哪里

- commands：`commands/zc/*.md`
- skills：`skills/zc-*/SKILL.md`
- agents：`agents/zc-*.md`
- 如果入口页不足以判断，就先打开对应 command、skill 或 agent 再继续

## 已安装能力

- 清单来源：`/home/runner/work/zc-ai-coding-toolkit/zc-ai-coding-toolkit/packages/toolkit/src/content`
- 匹配到的资产：75
- 命令入口：29 个，统一暴露为 `zc:<command>`
- skills：38 个
- agents：8 个

- `skill` `skill:api-and-interface-design`: API 与接口设计
- `skill` `skill:brainstorming-and-design`: 方案探索
- `skill` `skill:branch-finish-and-cleanup`: 分支收尾与清理
- `skill` `skill:browser-qa-testing`: 浏览器质检
- `skill` `skill:ci-cd-and-automation`: CI/CD 自动化
- `skill` `skill:code-review-and-quality`: 代码审查与质量
- `skill` `skill:code-simplification`: 代码简化
- `skill` `skill:codebase-onboarding`: 代码库导览
- `skill` `skill:context-budget-audit`: 上下文审计
- `skill` `skill:context-engineering`: 上下文工程
- `skill` `skill:continuous-learning`: 持续学习
- `skill` `skill:debugging-and-error-recovery`: 调试与恢复
- `skill` `skill:deprecation-and-migration`: 迁移与废弃
- `skill` `skill:developer-experience-audit`: 开发者体验审计
- `skill` `skill:documentation-and-adrs`: 文档与 ADR
- `skill` `skill:engineering-principles`: 工程原则
- `skill` `skill:frontend-ui-engineering`: 前端界面工程
- `skill` `skill:git-workflow-and-versioning`: Git 工作流
- `skill` `skill:idea-refine`: 想法细化
- `skill` `skill:incremental-implementation`: 增量实现
- `skill` `skill:multi-perspective-review`: 多视角评审
- `skill` `skill:parallel-agent-dispatch`: 并行调度
- `skill` `skill:performance-optimization`: 性能优化
- `skill` `skill:planning-and-task-breakdown`: 任务拆解
- `skill` `skill:release-documentation-sync`: 发布后文档同步
- `skill` `skill:review-response-and-resolution`: 审查响应与问题收敛
- `skill` `skill:safety-guardrails`: 安全护栏
- `skill` `skill:sdd-tdd-workflow`: SDD+TDD 工作流
- `skill` `skill:security-and-hardening`: 安全加固
- `skill` `skill:shipping-and-launch`: 发布上线
- `skill` `skill:source-driven-development`: 官方文档实现
- `skill` `skill:spec-driven-development`: 规格驱动开发
- `skill` `skill:sprint-retrospective`: 迭代回顾
- `skill` `skill:subagent-driven-development`: 子代理驱动开发
- `skill` `skill:team-orchestration`: 团队编排
- `skill` `skill:test-driven-development`: 测试驱动开发
- `skill` `skill:using-agent-skills`: 技能发现
- `skill` `skill:verification-before-completion`: 完成前验证
- `command` `command:api`: API
- `command` `command:build`: 构建
- `command` `command:careful`: 预警
- `command` `command:ci`: CI/CD
- `command` `command:commit`: 提交
- `command` `command:ctx-health`: 上下文
- `command` `command:debug`: 调试
- `command` `command:doc`: 文档
- `command` `command:freeze`: 锁定
- `command` `command:guard`: 防护
- `command` `command:idea`: 想法
- `command` `command:learn`: 学习
- `command` `command:migrate`: 迁移
- `command` `command:onboard`: 上手
- `command` `command:perf`: 性能
- `command` `command:plan-review`: 方案评审
- `command` `command:product-analysis`: 产品分析
- `command` `command:qa`: 浏览器质检
- `command` `command:quality-review`: 审查
- `command` `command:retro`: 复盘
- `command` `command:sdd-tdd`: 工作流
- `command` `command:secure`: 安全
- `command` `command:ship`: 发布
- `command` `command:simplify`: 简化
- `command` `command:spec`: 规格
- `command` `command:start`: 开始
- `command` `command:task-plan`: 计划
- `command` `command:ui`: 界面
- `command` `command:verify`: 验证
- `agent` `agent:architect`: 架构师
- `agent` `agent:backend-specialist`: 后端工程师
- `agent` `agent:code-reviewer`: 代码审查
- `agent` `agent:frontend-specialist`: 前端工程师
- `agent` `agent:performance-engineer`: 性能工程师
- `agent` `agent:product-owner`: 产品负责人
- `agent` `agent:security-auditor`: 安全审计
- `agent` `agent:test-engineer`: 测试工程师
