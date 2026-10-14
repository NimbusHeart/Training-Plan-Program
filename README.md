# Training-Plan-Program
大创项目仓库平台用于更新和整合项目代码资源

## 基础工程说明

仓库当前存放的是项目的基础工程：一份 STM32F407VGTx 的标准外设库模板，库文件与工程配置已就绪，后续功能在它之上继续添加。

- **芯片型号**：STM32F407VGTx
- **库与内核**：STM32F4xx 标准外设库（StdPeriph_Driver）+ CMSIS 内核文件
- **开发环境**：Keil MDK（uVision），工程文件为根目录下的 `Stm32_RVMDK.uvprojx`
- **程序入口**：`User/main.c`；库裁剪配置 `User/stm32f4xx_conf.h`；中断服务 `User/stm32f4xx_it.c`

### 目录结构

| 目录 | 说明 |
| --- | --- |
| `Libaries/arm` | 各型号启动文件，当前工程使用 `startup_stm32f40xx.s` |
| `Libaries/core` | 器件头文件 `stm32f4xx.h`、`system_stm32f4xx.c`，以及 CMSIS 内核头文件（`core_cm4.h` 等，取自 ARM CMSIS 5.9.0） |
| `Libaries/STM32F4xx_StdPeriph_Driver` | 标准外设库源码（`src`）与头文件（`inc`） |
| `User` | 主程序、中断服务、库配置 |
| `DebugConfig` | 调试器配置 |
| `Project/Basic`、`Project/Hardware` | 预留空目录，用于放置后续新增的底层代码与外设驱动 |
| `Output`、`Listings` | 编译产物输出目录，不入库 |

### 上手步骤

1. 用 Keil MDK 打开根目录下的 `Stm32_RVMDK.uvprojx`
2. 新增的 `.c` / `.h` 文件放进 `User/`，或放进 `Project/Basic`、`Project/Hardware`，再在工程里 Add Group / Add Files 挂上去
3. 如果新增了头文件目录，到 Options for Target → C/C++ → Include Paths 里补上路径
4. 编译产物写在 `Output/` 和 `Listings/`，已被 `.gitignore` 忽略；提交前建议先跑一次 `keilkill.bat` 清理
