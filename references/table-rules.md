# 表格字段与项目适配

## 默认字段

| 字段 | 含义与写法 |
| --- | --- |
| No. | 连续序号，不是物理行号 |
| Module | 工作大类，如 Baseline、BSP、MCU、Test |
| Category | 子类，如 Board Bring-up、Driver / Firmware |
| Feature | 具体工作对象，注明已知型号及数量 |
| Note | 做什么、达到什么基本目标；一条简短句子 |
| Cost (MM) | 人月；未要求估算则留空 |
| Quotation | 报价信息，未提供则留空，不从 MM 自动换算 |
| Comments | 依赖、前提、排除项、待确认信息 |

默认用上述八列，不同时建立同义的“评估范围”列。已有表的 Cost（MM）等命名保留。中文/英文 Note 对照列仅在用户要求时增加；没有特殊要求时可中文沟通、简单英文入表。

## Note 示例

以下为写法参考，不是必须纳入的工作范围。

| 工作项 | 中文 Note | 简单英文 Note |
| --- | --- | --- |
| Build and Flash Environment Setup | 配置编译和烧录环境，完成镜像编译与烧录。 | Set up the build and flashing environment and verify image build and flashing. |
| Source Baseline | 建立客户代码基线并集成所需供应商软件包。 | Set up the customer source baseline and required vendor packages. |
| Board Boot and Debug | 完成系统启动，使能 ADB、串口和日志。 | Boot the board and enable ADB, serial access and logs. |
| CAN | 完成已确认路数的 CAN 基础收发。 | Enable basic CAN transmit and receive on the specified channels. |
| SPI NOR | 完成器件识别及基础擦写读取。 | Detect the flash and verify basic erase, write and read. |
| Wi-Fi Module Bring-up | 完成模块供电、复位和主机接口识别。 | Verify module power, reset and host interface detection. |
| Basic Function Test | 完成范围内功能的基础测试。 | Run basic function tests for the agreed scope. |
| Stability Test | 长时间挂机，确认系统不死机。 | Verify that the system runs for an extended period without hanging or crashing. |
| Hardware Test Support | 配合硬件测试并定位相关问题。 | Support hardware testing and issue analysis. |

示例中的接口仅适用于资料确认的项目。不要给所有板卡添加 ADB。稳定性测试不擅自添加 72 小时、压力负载或温度条件；如需正式验收阈值，另行确认。

## 按项目选择粒度

- EVK/载板：可按 SoC 基础启动、独立外设链路、MCU 子系统划分。两路同型号器件可写在一项中并注明数量，不直接把单路人力乘二。
- 音频：音频主芯片、DAC、A2B 是否拆项取决于独立适配工作。拆项时标明各自边界；天线、插座和连接器通常归入关联 Note 或 Comments。
- 摄像头：区分摄像头数量、串/解串器数量和 CSI lane 数。lane 数不是摄像头数量；标注冲突先确认。
- MCU：按裸机/FreeRTOS/AUTOSAR 分组，各组可包含 Bring-up、PMIC、CAN、LIN、风扇、Flash、Ethernet。主机通信说明两端职责；不要把 SoC 的 CAN 算成 MCU 的 CAN。
- 认证：基础环境、模块 Bring-up、驱动/固件、平台集成与认证工具/准备/支持/交付按资料拆分。已有 CE/NCC、WFA 工作块保留；“认证支持”不等于承诺拿证。
- Test 默认整体一条。用户另行要求稳定性或 Hardware Test Support 时单列，明确它与开发自测、基础功能测试的区别。
- 电源器件不必都有软件驱动：已确认在范围内可写上电/配置验证，控制方式未知时说明待确认，不能根据芯片框图虚构接口。
- Build Environment 与 Flashing、Boot 与 Debug 可合并为一个工作包。驱动与固件适配、测试工具开发与认证支持是否合并，以实际边界为准。

## Comments 示例

- Customer BSP and vendor driver source are required.
- Device model is not provided.
- Customer provides the base test tool and test firmware.
- Certification fees are not included.（仅限用户已确认此排除项）

必要假设写 Comments 或表前说明；不要在 Note 堆积项目风险、长流程或未授权的完成标准。
