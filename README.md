# STM32_learning

- 资源
  - [野火产品资料下载中心 — 野火产品资料下载中心 文档 (embedfire.com)](https://doc.embedfire.com/products/link/zh/latest/index.html)
  - [150集-野火F103霸道/指南者视频教程](https://www.bilibili.com/video/BV1Xs411g7Aj/?spm_id_from=333.999.0.0&vd_source=e4455003e32fdc49fb1b368513cd60bd)



- 文件夹结构

  - 00_STM32官方资料
  - 01\_野火指南者\_源码教程
  - 02\_野火指南者\_开发板资料

  

## 01\_野火指南者\_源码教程

### 00\_开机测试例程

- 整版硬件测试
  - 开机测试
    - **需要刷写出厂测试程序**
      - ./Project/RVMDK(uv5)/iSO-STM32.uvprojx
      - build
      - download
  - APP 使用说明
    - 介绍出厂测试程序的使用方法
- 开发板硬件资源简介



### 01_标准库教程笔记

#### 第 1 章 前言与学习必读

- 参考资料
  - 《STM32F10x-中文参考手册》
  - 《Cortex-M3 权威指南》
- 每章的主要内容
  - 外设简介
  - 外设功能框图分析
  - 代码讲解
- 配套硬件
  - 野火 STM32-F103VE-指南者



#### 第 2 章 如何安装 KEIL5 和打开例程

##### 安装 Keil 5 与 STM32 芯片包 

- 安装 Keil 5 
  - 官网下载：
    - [Keil Product Downloads](https://www.keil.com/download/product/)
    - 下载 MDK-ARM
  - 百度网盘
    - [KEIL和芯片包_免费高速下载|百度网盘-分享无限制 (baidu.com)](https://pan.baidu.com/s/1QlyvCgg-ZYLomvp8tOtDtw#list/path=%2F)
  - 注意
    - 不要使用中文安装路径
    - KEIL5 的安装目录不能跟其他版本的 KEIL 冲突
    - 教育用户有编译大小限制，需要注册为Pro用户
- 安装 STM32 芯片包 
  - 官网下载：http://www.keil.com/dd2/pack/
  - 把下载好的包双击安装即可，安装路径选择跟 KEIL5 一样的安装路径，安装成功之后，在 KEIL5的 Pack Installer 中就可以看到我们安装的包
  - 新建工程的时候，就有对应的单片机的型号可选



##### KEIL5 简介

- ##### 如何打开工程文件

  - 直接找到.uvprojx 后缀名文件

  - 以工程模板形式打开项目
    - .uvprojx 文件主要存放在 Project 文件夹下

- 主界面
  - 菜单栏：包含 File 文件、Edit 编辑、View 视图、Project 工程、Help 帮助等
  - 工具栏：常见工具的快捷按钮，
    - 仿真类快捷按钮：在进行仿真时使用，具有断电标记作用
    - 编译类快捷按钮：对代码进行编译下载
    - 工程目标选项又称魔术棒：即对工程目标的配置，如芯片设备选择、C/C++ 选项、仿真配置等等
  - 工程窗口：主要显示项目内容，文件组、源文件和头文件等
  - 编辑窗口：编写代码的地方
  - 消息窗口：反馈编译信息、烧录信息等
  - 状态栏：光标的行列位置、字符编码、键盘 NUM 锁定等一些状态信息



#### 第 3 章 如何用 DAP 仿真器下载程序

##### 仿真器  Fire-Debugger

- 遵循 ARM 公司的 CMSIS-DAP 标准
- 支持所有基于 Cortex-M内核的单片机如 M3，M4，M7
- 支持下载和在线仿真程序
- 支持Windows，免驱
- 支持 KEIL、IAR
- 支持
  - JTAG (20Pin)
  - SWD (5Pin)
  - V-UART (4Pin)

##### 仿真器硬件连接

- win<--->USB<--->Fire DAP仿真器<--->JTAG排线<--->开发板（开发板本身需要上电）

##### 仿真器配置

- Debug
  - Use: CMSIS-DAP Debugger
  - Settings: 
    - Debug:
      - JTAG/SW Adapter
        - 自动识别为 fireDAP CMSIS-DAP
      - SW接口
        - 选择SW接口
        - 勾选SWJ
        - Max Clock 5MHz
      - SW Device
        - SWDIO: 连接了开发板并上电后，仿真器会识别开发板芯片
      - Reset:
        - 老版Keil 5: Autodetect
        - Keil 5 (v5.36): SYSRESETREQ(Default)
      - 注意
        - 如果是普通 DAP 记得打开我们提供的写好的每一个工程后，在仿真器配置界面左下角改选为 Connect：under Reset 才能下载。
        - 普通 DAP 要试 Debug 时，Reset 选择 HW RESET 或者 VECTRESTET 这样在 Debug 时可
    - Flash Download 选择目标板
      - 选择 Erase Section
        - 选择 fullchip 非常慢
      - 勾选 Verify, Reset and Run 自动运行，无需复位
      - Programming Algorithm
        - 显示对应的芯片算法
- Utilities
  - Use Debug Driver

##### 仿真器编译下载

- build
  - 教育证书有编译大小限制，注册为Pro用户
- load



#### 第 4 章 如何用串口下载程序

