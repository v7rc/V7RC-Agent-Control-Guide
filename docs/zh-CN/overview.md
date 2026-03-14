# 总览

## 目的

本 Repository 定义 AI Agent 应如何安全且一致地控制 V7RC 机器人。

原始 V7RC Protocol 侧重于底层消息格式。
本项目补充了：
- 语义化控制说明
- 硬件映射
- 安全边界
- 可复用的 robot profile
- OpenClaw 等系统的集成方式

## 三层结构

### 第 1 层：Raw protocol
例如：
- `SRT1500150015001500#`
- `SRV1500150015001500#`
- `CMDSTOP           #`

### 第 2 层：硬件映射
例如：
- C1 = 左右移动
- C2 = 前进后退
- C4 = 转向
- LED = 前方状态灯

### 第 3 层：Agent Intent
例如：
- `stop`
- `move_forward_slow`
- `turn_left`
- `ready_led`

## 设计原则

1. 安全优先
2. 优先使用明确映射，不做猜测
3. Profile 需要可供机器解析
4. 允许不同机型差异
5. 不允许 AI 自创未支持命令
