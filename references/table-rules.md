# 表格字段与项目适配

## 默认字段

| 字段 | 含义与写法 |
| --- | --- |
| No. | 连续序号，不是物理行号 |
| Module | 工作大类，如 Baseline、BSP、MCU、Test |
| Category | 子类，如 Board Bring-up、Driver / Firmware |
| Feature | 具体工作对象，注明已知型号及数量 |
| Note | 做什么、达到什么目标；简短描述 |
| Cost (MM) | 人月；未要求估算则留空 |
| Quotation | 报价信息，未提供则留空，不从 MM 自动换算 |
| Comments | 依赖、前提、排除项、待确认信息 |

上述八列是参考结构，按用户要求选择列和语言；避免增加同义的重复字段。

## Note 示例

以下为写法参考，不是必须纳入的工作范围。

| 工作项 | 中文 Note | 简单英文 Note |
| --- | --- | --- |
| Build Environment Setup | 配置编译环境并完成目标镜像编译。 | Set up the build environment and build the target image. |
| Source Baseline | 建立客户代码基线并集成所需供应商软件包。 | Set up the customer source baseline and required vendor packages. |
| Board Bring-up | 完成板卡启动并验证所需调试接口。 | Boot the board and verify the required debug interfaces. |
| CAN | 完成已确认路数的 CAN 基础收发。 | Enable basic CAN transmit and receive on the specified channels. |
| SPI NOR | 完成器件识别及基础擦写读取。 | Detect the flash and verify basic erase, write and read. |
| Wi-Fi Module Bring-up | 完成模块供电、复位和主机接口识别。 | Verify module power, reset and host interface detection. |
| Basic Function Test | 完成范围内功能的基础测试。 | Run basic function tests for the agreed scope. |
| Stability Test | 按约定条件执行稳定性测试并记录结果。 | Run stability tests under the agreed conditions and record the results. |
| Hardware Test Support | 配合硬件测试并定位相关问题。 | Support hardware testing and issue analysis. |

示例仅展示句式。具体接口、功能深度、测试条件和验收标准来自项目资料；未明确的关键条件列为待确认。

## 按项目选择粒度

- 按工作目标、实现边界和验证方式确定粒度；不按框图方框数量或开发步骤数机械拆项。
- 名称或功能相近不等于同一工作项。实现不同、依赖不同或可独立验收时分别列项；属于同一目标且无法独立评估时可合并，并说明覆盖范围。
- 同型号多实例注明数量，结合复用程度和独立联调工作评估，不机械倍增人力。
- 区分设备数量、物理通道数和协议资源数，不互相换算或相乘。
- 跨处理器、板卡或软件层的工作说明两端职责与公共部分，避免重复计入。
- 硬件器件存在不代表需要开发驱动；依据控制方式和软件职责判断工作内容。
- 测试按功能、条件、目标和独立工作量决定是否拆分，不固定行数；与开发自测的边界要明确。
- 支持类工作与最终结果承诺分别描述，例如测试支持不自动包含认证通过承诺。

## Comments 示例

- Customer BSP and vendor driver source are required.
- Device model is not provided.
- Customer provides the base test tool and test firmware.
- Certification fees are not included.（仅限用户已确认此排除项）

必要假设写 Comments 或表前说明；不要在 Note 堆积项目风险、长流程或未授权的完成标准。
