# Metro Basin

**城市轨道交通实时运行状态重建与运输分析**  
Urban Rail Transit Operational State Reconstruction and Transport Analytics

## 项目简介 · Overview

Metro Basin 是以成都轨道交通为应用案例的独立技术项目，通过离散列车观测、线路拓扑、车次链关联及自定义车站电报码，重建列车运行状态、实际运行交路与逐站时刻表，并通过标准化 API 和 SwiftUI 客户端展示实时运营信息。

Metro Basin reconstructs urban rail transit operational states, train routes and observed timetables from discrete train observations, network topology and train-run associations. Its standardized APIs support real-time visualization in a SwiftUI client.

## 技术文档 · Documentation

| 文档 | 阅读入口 |
|---|---|
| 城市轨道交通实时运行状态重建 | [Markdown 在线阅读](Metro_Basin_Operational_State_Reconstruction_ZH.md) |
| 正式排版白皮书 | [PDF](Metro_Basin_实时运行状态重建.pdf) |

Markdown 为持续更新的技术文档，PDF 为发布时的排版快照，两者更新日期可能不同。

## 核心技术 · Core Methods

- S/A/E 虚拟站点编码与列车运行状态表达
- 车次链关联、始发与实际交路推断
- 环线接续、大小交路及直达车处理
- 基于离散观测的逐站时刻表重建
- 19 条线路的统一车站电报码体系
- 七个运营日内的车辆历史观测与配属展示
- SwiftUI 实时线路图、车站大屏及延时运营动态适配

## 技术架构 · Architecture

```text
离散列车观测 / Train observations
    |
    v
数据标准化与拓扑匹配 / Normalization & topology
    |
    v
S/A/E 运行状态重建 / State reconstruction
    |
    +--> 车次链与交路识别 / Route inference
    |        |
    |        +--> 历史观测与时刻表重建 / History & timetables
    |                    |
    v                    v
标准化 API / API Architecture <--- 运营时段与延时配置
    |
    v
SwiftUI 移动端 / iOS client
```

## 核心接口架构 · API Architecture

| 功能 | GET 相对路径 |
|---|---|
| 实时列车 | `/api/trains` |
| 单车详情 | `/api/trains/detail` |
| 车站最近列车 | `/api/trains/nearby` |
| 车站编码 | `/api/trains/stations` |
| 观测时刻表 | `/api/trains/timetable` |
| 历史观测 | `/api/trains/fleet/history` |
| 延时运营日 | `/api/trains/extension-days` |

仅展示接口相对路径与设计结构，不公开实际服务入口。具体参数及字段见技术白皮书。

## 数据与发布说明 · Data and Publication

本仓库当前公开技术文档，不包含完整服务端或客户端源码。文档中的接口样例为模拟数据；重建时刻不等同于精确实测时刻。本项目非轨道交通运营方官方项目。部分推断方法的适用边界及验证状态见白皮书。

## Copyright

© 2026 Metro Basin. All rights reserved unless otherwise stated.
