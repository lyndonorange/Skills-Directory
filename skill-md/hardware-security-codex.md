---
name: hardware-security
display_name: hardware-security
platform: Codex
category: General and specialized workflows
---

# hardware-security - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `hardware-security` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Use for authorized hardware and embedded interface security research including UART/JTAG discovery, debug pad triage, secure boot overview, and offline firmware extraction support.

## How To Use It In Codex

In Codex, click the chat box, press /, choose hardware-security, then write the task. Fallback prompt: Use the hardware-security skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `hardware-security` |
| Canonical name | `hardware-security` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

Use for authorized hardware and embedded interface security research including UART/JTAG discovery, debug pad triage, secure boot overview, and offline firmware extraction support.


## Original SKILL.md

---
name: hardware-security
description: Use for authorized hardware and embedded interface security research including UART/JTAG discovery, debug pad triage, secure boot overview, and offline firmware extraction support.
---

# Hardware / Embedded Interface Security

## ACTION REQUIRED（读完后立刻执行）

1. `NOW`: 确认**物理接触授权**与设备归属
2. `NOW`: ESD/电源安全；默认只读探测
3. `NEXT`: 联合 firmware-pentest 做镜像分析
4. `ACT`: 外壳与调试接口识别 →  consoles → 提取

## 适用场景

- UART / JTAG / SWD 调试口发现
- 启动日志、root shell、引导打断
- 配合拆机提取 Flash
- 安全启动/加密 Flash 的可行性评估（非破坏性优先）

## 工作流

```text
□ 拆解授权设备；拍照标注测试点
□ 万用表找 GND/VCC/TX/RX；逻辑电平 1.8/3.3/5V
□ USB-TTL 只读日志；记录波特率
□ JTAG：枚举 IDCODE；评估是否锁定
□ 提取镜像 → 交接 firmware-pentest / ghidra
```

## 工具链

| 工具 | 用途 |
|------|------|
| USB-TTL / logic analyzer | UART |
| J-Link / CMSIS-DAP | 调试 |
| bus pirate / flipper（实验室） | 多协议 |
| binwalk / flashrom | 提取 |

## 参考

- `references/debug-interface-triage.md`
- `../firmware-pentest/` `../ot-ics/`

## 路由上下文

**上游**: MASTER R34
**MUST NOT**: 未授权拆机/损坏他人设备

## 任务完成自检

- [ ] 是否记录接口电平与引脚图？
- [ ] 镜像是否哈希保全？
- [ ] Checklist？
