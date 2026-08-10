---
name: database-security
display_name: database-security
platform: Universal Agents
category: Data, analytics, and databases
---

# database-security - Universal Agents Skill Package

## What This Is

This is a friend-safe Markdown copy of `database-security` for Universal Agents. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Use for authorized database security assessment covering PostgreSQL/MySQL/MSSQL/Mongo/Redis exposure, authz, UDF/command paths, and misconfiguration review.

## How To Use It In Universal Agents

In tools that read ~/.agents/skills, type: Use the database-security skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `database-security` |
| Canonical name | `database-security` |
| Platform | `Universal Agents` |
| Category | Data, analytics, and databases |

## Description

Use for authorized database security assessment covering PostgreSQL/MySQL/MSSQL/Mongo/Redis exposure, authz, UDF/command paths, and misconfiguration review.


## Original SKILL.md

---
name: database-security
description: Use for authorized database security assessment covering PostgreSQL/MySQL/MSSQL/Mongo/Redis exposure, authz, UDF/command paths, and misconfiguration review.
---

# Database Security Assessment

## ACTION REQUIRED（读完后立刻执行）

1. `NOW`: 读取 precedent-pentest；**生产库禁止破坏性语句** unless 明确允许
2. `NOW`: scope 写清实例、账号权限、是否允许写/删
3. `NEXT`: 客户端工具路径
4. `ACT`: 暴露面 → 认证 → 授权 → 配置 → 利用链验证（安全）

## 适用场景

- 数据库未授权/弱口令/错误绑定 0.0.0.0
- 权限过大、危险功能（xp_cmdshell、COPY PROGRAM、UDF）
- 横向：从应用账号到 DBA
- NoSQL 注入与 Redis 写文件等（授权环境）

## 工作流

```text
□ 网络暴露与 TLS
□ 账号角色与 grantee
□ 敏感表访问控制
□ 危险配置：file_priv、xp_cmdshell、load_file
□ 审计日志是否开启
□ 备份与快照权限
```

## 工具链

| 工具 | 用途 |
|------|------|
| 官方 CLI | 连接与枚举 |
| sqlmap | 注入验证（授权） |
| nuclei | 已知暴露模板 |
| 云 RDS 控制台审计 | 配置 |

## 参考

- `references/db-misconfig-checklist.md`
- `../pentest-tools/` `../cloud-k8s/`

## 路由上下文

**上游**: MASTER R35
**下游**: 获 OS 命令 → attack-chain；云托管 → cloud-k8s

## 任务完成自检

- [ ] 是否避免未授权写删？
- [ ] 是否区分配置问题与可利用链？
- [ ] Checklist？
