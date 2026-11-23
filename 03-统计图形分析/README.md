# 03｜统计图形分析：RAWGraphs 源码研究

> 研究对象：[rawgraphs/rawgraphs-app](https://github.com/rawgraphs/rawgraphs-app)（RAWGraphs 网页应用源码仓库）。本专题同时追踪其直接依赖的 [rawgraphs-charts](https://github.com/rawgraphs/rawgraphs-charts) 图表实现库与 [rawgraphs-core](https://github.com/rawgraphs/rawgraphs-core) 核心引擎文档。  
> 研究基准：GitHub 默认分支 `master`；本次检查的 app 源码树 SHA：`48c3b2ee9ff412721a2c99c7bed38e734b3fa534`。源码会持续变化，本文结论对应本次读取的版本。

## 一、研究定位

RAWGraphs 是一个面向设计师与数据可视化实践者的开放式网页工具。它以表格数据为输入，通过图表模型与数据映射生成 SVG 等矢量可视化结果，连接电子表格与矢量图形编辑软件。它不仅提供图表类型，还提供数据解析、字段映射、视觉参数调整、渲染与导出的一整套工作流。

本专题的目标不是照搬程序，而是从源码中提取可用于信息可视化学习、图形分类、案例判断与设计实践的知识。

## 二、研究内容导航

1. [系统架构与工作流程](01-系统架构与工作流程.md)：应用层、图表库、核心引擎的分工；五阶段工作流。
2. [统计图形类型目录](02-统计图形类型目录.md)：按源码登记的 32 种内置图表整理名称、表达任务与官方类别标签。
3. [数据映射与视觉编码](03-数据映射与视觉编码.md)：数据类型、图形维度、映射关系、聚合与视觉变量。
4. [图形分析与评价方法](04-图形分析与评价方法.md)：将源码结构转化为可执行的图表分析框架。
5. [源码索引与研究边界](05-源码索引与研究边界.md)：关键源码位置、依据等级、需要避免的误读。

## 三、关键结论

- RAWGraphs 以**单一表格数据集**为主要输入，列具有字段名，字段值需识别为字符串、数值或日期等数据类型。
- 用户选择的不是一个静态图片，而是一个**视觉模型（visual model）**；图表实现定义维度、数据映射、视觉选项和渲染方法。
- 数据字段与图表维度之间通过 **mapping** 建立联系；图表的 `mapData` 再将原始表格转换为适合该图形的结构。
- 数据映射与图形渲染分离，使视觉参数调整时可以避免重复执行全部数据转换。
- 图表库的官方类别标签包括 correlations、proportions、distributions、time series、networks、hierarchies。它们是可重叠的筛选标签，不是互斥的图表学分类体系。
- 最终输出以 SVG 为核心，也支持 PNG、JPG 与 RAWGraphs 项目文件；SVG 便于在矢量编辑软件中继续修改。

## 四、研究时的区分原则

- **源码事实**：程序中实际登记的图表、字段、函数、配置项和工作流程。
- **图形学解释**：根据图表结构解释它表达的数据关系与视觉编码。
- **设计评价**：对可读性、比较效率、认知负担、适用场景的分析，需结合具体图形与数据，不冒充源码原文。
- **待核实内容**：源码没有明确说明的统计假设、计算细节或适用边界，单独标注，不凭图名推断。

## 五、上游项目

- [RAWGraphs App](https://github.com/rawgraphs/rawgraphs-app)
- [RAWGraphs Charts](https://github.com/rawgraphs/rawgraphs-charts)
- [RAWGraphs Core](https://github.com/rawgraphs/rawgraphs-core)
- [RAWGraphs 官方网站](https://www.rawgraphs.io/)

许可：上述项目仓库声明采用 Apache License 2.0。引用或复用源码、图表缩略图和其他资源时，应遵守相应仓库的许可与署名要求。
