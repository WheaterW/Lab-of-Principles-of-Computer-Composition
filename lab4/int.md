### 第1关：RISC-V指令译码器设计

100

- 任务要求
- 评论

- [实验目的](https://www.educoder.net/tasks/46fzoyba7xqf#实验目的)
- [实验内容](https://www.educoder.net/tasks/46fzoyba7xqf#实验内容)
- [电路引脚](https://www.educoder.net/tasks/46fzoyba7xqf#电路引脚)
- [电路框架](https://www.educoder.net/tasks/46fzoyba7xqf#电路框架)
- [电路测试](https://www.educoder.net/tasks/46fzoyba7xqf#电路测试)
- [测试输出结果说明](https://www.educoder.net/tasks/46fzoyba7xqf#测试输出结果说明)
- [调试技巧与常见故障](https://www.educoder.net/tasks/46fzoyba7xqf#调试技巧与常见故障)

------

#### 实验目的

帮助学生理解指令译码的基本概念，能将32位RISC-V指令字译码成不同的指令译码信号。

#### 实验内容

利用比较器等功能模块将32位RiscV指令字译码生成LW、SW、BEQ、SLT、ADDI、OtherInstr等指令译码信号：

![img](https://data.educoder.net/api/attachments/756063) 指令译码器是控制器核心功能部件，负责将指令字翻译成一根根的指令译码信号，每一根指令译码信号代表一条具体的指令，如上图中的I1...Im。

#### 电路引脚

| 信号       | 位宽 | 功能描述                    |
| ---------- | ---- | --------------------------- |
| IR         | 32   | RISC-V指令字 IR             |
| LW         | 1    | 当前指令为lw指令时输出为1   |
| SW         | 1    | 当前指令为sw指令时输出为1   |
| BEQ        | 1    | 当前指令为beq指令时输出为1  |
| ADDI       | 1    | 当前指令为addi指令时输出为1 |
| SLT        | 1    | 当前指令为slt指令时输出为1  |
| OtherInstr | 1    | 当前指令为其它指令时输出为1 |

子电路外观如下： ![img](https://data.educoder.net/api/attachments/754582)

#### 电路框架

RiscVOnBusCpu-1.circ  ◇指令译码器  子电路 ![,](https://data.educoder.net/api/attachments/2077494) **注意：可以整体平移引脚框到电路任何位置，但由于电路封装与引脚位置和顺序有关系，所以框内引脚一律不许增删改，哪怕是移动位置调整顺序，改变引脚朝向，也不要在电路中增加额外的引脚，否则测试系统无法测试**。

#### 电路测试

完成设计后，可利用文本编辑工具打开 RiscVOnBusCpu-1.circ，将所有文字信息复制粘贴到 Educoder 平台的代码框中，再点击评测按钮即可进行本关测试。平台会对你设计的电路进行自动测试，为方便测试，请勿修改子电路封装。

#### 测试输出结果说明

最终输出包括个检测引脚的期望值和实际值，出错时请对比查错。

| #    | 信号       | 功能描述                         |
| ---- | ---------- | -------------------------------- |
| 1    | Cnt        | 测试用例编号，注意是**十六进制** |
| 2    | IR         | 指令字IR的值                     |
| 3    | LW         | 1                                |
| 4    | SW         | 1                                |
| 5    | BEQ        | 1                                |
| 6    | ADDI       | 1                                |
| 7    | SLT        | 1                                |
| 8    | OtherInstr | 1                                |

本关测试用例如下：

### 第2关：支持中断的微程序入口查找逻辑

100

- 任务要求
- 评论

- [实验目的](https://www.educoder.net/tasks/9mzu42gplqaw#实验目的)
- [实验内容](https://www.educoder.net/tasks/9mzu42gplqaw#实验内容)
- [实验步骤](https://www.educoder.net/tasks/9mzu42gplqaw#实验步骤)
- [电路框架](https://www.educoder.net/tasks/9mzu42gplqaw#电路框架)
- [电路引脚](https://www.educoder.net/tasks/9mzu42gplqaw#电路引脚)
- [电路测试](https://www.educoder.net/tasks/9mzu42gplqaw#电路测试)

------

#### 实验目的

了解微程序控制器中微程序分支的基本原理，为已经实现的微程序入口查找逻辑增加eret对应微程序入口查找逻辑，要求重新设计微程序入口查找逻辑。 ![img](https://data.educoder.net/api/attachments/759819)

#### 实验内容

![img](https://data.educoder.net/api/attachments/759824) 设计如上电路，根据指令译码信号生成5位的微程序入口地址，地址转移逻辑如下： ![img](https://data.educoder.net/api/attachments/759833)

#### 实验步骤

1. 填写6号EXCEL表格中的微程序入口地址表格 ![img](https://data.educoder.net/api/attachments/761290) ![img](https://data.educoder.net/api/attachments/761399)
2. 自动生成逻辑表达式 ![img](https://data.educoder.net/api/attachments/761300)
3. 在logisim中利用分析组合逻辑电路功能自动生成电路

#### 电路框架

RiscVOnBusCpu-1.circ  ◇微程序地址转移逻辑  子电路

#### 电路引脚

| 信号  | 输入/输出 | 位宽 | 功能描述            |
| ----- | --------- | ---- | ------------------- |
| LW    | 输入      | 1 位 | LW 指令指令译码信号 |
| SW    | 输入      | 1 位 | SW 指令译码信号     |
| BEQ   | 输入      | 1 位 | BEQ 指令译码信号    |
| ADDI  | 输入      | 1位  | ADDI指令译码信号    |
| SLT   | 输入      | 1 位 | SLT指令译码信号     |
| MERET | 输入      | 1 位 | MERET指令译码信号   |
| S4~S0 | 输出      | 1 位 | 微程序地址入口地址  |

子电路外观： ![img](https://data.educoder.net/api/attachments/758554)

#### 电路测试

确认微程序地址转移逻辑电路完成后，可利用文本编辑工具打开 RiscVOnBusCpu-1.circ，将所有文字信息复制粘贴到 Educoder 平台的 代码框架中，再点击评测按钮即可进行本关测试。平台会对你设计的电路进行自动测试，为方便测试，请勿修改子电路封装，本关测试用例如下: