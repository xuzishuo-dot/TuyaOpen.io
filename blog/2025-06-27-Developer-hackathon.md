---
slug: /52hrs-hackathon-with-tuyaopen
title: '52小时-创业森林 黑客松大赛'
authors: [tuya,hsuanhanlai]
image: /img/home/tuyaopen-logo-social-preview.png
tags: [TuyaOpen, Hackathon, Contest]
---


![event](https://images.tuyacn.com/fe-static/docs/img/6d005a49-7b92-4602-af60-b7acca333eab.png)

> **此文档为大赛专用文档，为参赛者提供 总览指引。**

### 比赛信息：
大赛时间：6/27~6/29 【52小时】


# 重要资源：
- 涂鸦大赛PPT ---> [PPT 介绍](https://tuyaopen-pu9rufi.gamma.site/)
- TuyaOpen 代码仓库 ---> [Github](https://github.com/tuya/TuyaOpen)
- TuyaOpen 文档官网 ---> [tuyaopen.ai](https://tuyaopen.ai)


## TuyaOpen vs TuyaOS
TuyaOpen 是从行业领先的 TuyaOS 架构开源的。经过全球 130 万开发者的验证，它提供了一个定义良好的 API，用于开发支持不同 MCU 的 C/C++ 应用程序。抽象了外设连接、云连接和安全性的复杂性。此框架通过简单的编码体验加速您的开发过程，使您能够更快、更轻松地构建 AI+IoT 产品。

:::tip 怎么选？
大赛同学按照需求选用即可。目前如果有“视频AI”和"商业化"需求选TuyaOS，不然强烈建议TuyaOpen。TuyaOpen生态更加开放。
:::

### TuyaOpen vs TuyaOS 差异
| 功能                  | TuyaOpen                                         | TuyaOS                                                      |
|-----------------------|--------------------------------------------------|-------------------------------------------------------------|
| 目标用户              | 开源开发者                                        | 商业合作开发者                                              |
| 源代码获取            | 完全开源，源码可访问                               | 商用代码部分开源，支持二次开发                               |
| 代码下载              | GitHub、Gitee 免费开源下载                        | VSCode 插件 WindIDE + 邮箱授权获取代码                      |
| 开发环境              | Linux、Windows、Mac                               | 仅支持 Linux，其他平台需用虚拟机                             |
| Tuya Wukong 云端AI组件 | ✅                                                | ✅ 最新最快                                                  |
| Tuya Wukong 语音 AI ASR 能力 | ✅                                         | ✅                                                          |
| Tuya Wukong 视频 AI 能力    | ❌ 暂不支持                                  | ✅                                                          |
| Tuya 雲大模型定制化能力 （LLM/Prompt/Workflow/RAG）   | ✅                                  | ✅                                                          |
| 源码定制能力          | 高度源码定制                                      | API 级定制，链接库，商业功能组件更丰富                       |
| 芯片支持              | Tuya T 系列 / ESP 系列（详见支持列表）             | Tuya T 系列                                                 |
| 开发语言              | C/C++                                            | C/C++                                                       |
| 文档支持              | [TuyaOpen 官网](https://TuyaOpen.ai)              | [Tuya 开发者官网](https://developer.tuya.com/cn/docs/iot-device-dev) |
| 贡献源码或二次开源     | ✅                                                | 遵循 Copyright License                                      |
| 硬件生态              | 持续增加芯片、开发板和外设驱动                     | 采用推荐选型方案                                            |


# 嵌入式软件开发 
## TuyaOpen 专区
### 文档
- TuyaOpen 总文档：[docs](/docs/about-tuyaopen)
- AI API 代码模块: https://github.com/tuya/TuyaOpen/tree/master/src/tuya_ai_basic

### 示例总览
善用示例代码 减少开发成本避免重复造轮子。

- your chat bot: https://github.com/tuya/TuyaOpen/tree/master/apps/tuya.ai/your_chat_bot
    - T5/ESP32 跨平台支持示例
    - 语音ASR + Tuya 云端大模型
    - 连接 AI Prompt/Agent 能力
    - 情绪感知交互能力
    - 模块组件： `屏幕`+`Mic`+`Speaker`+`WIFI`+`按键`

- your chat bot: https://github.com/tuya/TuyaOpen/tree/master/apps/tuya.ai/your_chat_bot    
    - T5/ESP32 跨平台支持示例
    - 语音ASR + Tuya 云端大模型
    - 连接 AI Prompt/Agent 能力
    - 情绪感知交互能力
    - 做种唤醒模式
    - App 控制机器人交互
    - 情感识别 -> 动作的能力
    - 模块组件： `屏幕`+`Mic`+`Speaker`+`WIFI`+`按键` + `舵机`
- Switch Demo https://github.com/tuya/TuyaOpen/tree/master/apps/tuya_cloud/switch_demo
    - 基础原生示例演示设备作为 IoT LED 灯可连接至涂鸦云，被Tuya云服务/APP控制
    - DP 消息事件处理
    - 基础配网，硬件鉴权过程

- 基础组件Demo https://github.com/tuya/TuyaOpen/tree/master/examples
    - 蓝牙/WIFI
    - SPI I2C ADC 基础接口协议 Demo
    - 协议Demo
    - 屏幕渲染框架LVGL 示例
    等等....


## TuyaOS 专区
- WindIDE：Tuya Wind IDE 是面向基于 TuyaOS EasyGo 的开发者提供的一站式集成开发环境。
    - https://developer.tuya.com/cn/docs/iot-device-dev/tuyaos-wind-ide

    ## AI 基建 Tuya Wukong AI 嵌入式设备端
    - Tuya Wukong AI https://developer.tuya.com/cn/docs/iot-device-dev/ai-hardware?id=Kectwmx9isrgl
    - 能力地图： [link](https://developer.tuya.com/cn/docs/iot-device-dev/wukong-abi-map?id=Keedxu1netj62)
    - 多模态交互： [link](https://developer.tuya.com/cn/docs/iot-device-dev/tuyaos-wukong-capability-multi-media)


## Tuya云平台 零代码云端AI开发
- 注册 Tuya Developer 云服务
    - https://auth.tuya.com/register
- 文档：智能体开发平台
    - https://developer.tuya.com/cn/docs/iot/ai-agent-management?id=Kdxr4v7uv4fud

---

# 硬件开发板
## 开发板
### 涂鸦 T5AI Board 开发板
![T5-AI Board Pinout](https://images.tuyacn.com/fe-static/docs/img/6b7ab959-0635-4293-991b-b8dda293614b.jpg)

- 资料文档入口：[T5AI Board Overview](/zh/docs/hardware-specific/t5-ai-board/overview-t5-ai-board)
- I/O Pin脚高清下载：[Pinout](/docs/hardware/T5-AI-Board-Pinout-v102.pdf)
- 如何快速编译项目+烧写？：[教程](/docs/quick_start/enviroment-setup)

### 涂鸦T5 mini开发板 （第三方社区开发板）
- 优势是更小尺寸，适合空间要求较高方案。（社区开发板-文档不全）
- 使用上可以参考 [T5AI Board](/blog#%E6%B6%82%E9%B8%A6-t5ai-board-%E5%BC%80%E5%8F%91%E6%9D%BF) 功能相近。

### 地瓜机器人RDK X5
- 如何RDK和TuyaOpen整合? 🚧：【施工中】
- 资料文档入口：[RDK X5 文档入口](https://developer.d-robotics.cc/information)


---

# 现场资源
避免资源滥用，优先支持有明确idea团队领取/使用。也非常建议团队带自己熟悉的工具。
开发板必须选用大赛指定，但是外设和产品形态也非常鼓励自备携带参赛。

### 开发板
- [涂鸦T5 AI开发板](/zh/docs/hardware-specific/t5-ai-board/overview-t5-ai-board)	x15
- 涂鸦T5 mini开发板	x10
- 地瓜机器人RDK X5	x20
### 外设配件
- 喇叭（3020 4欧3瓦）	x20
- 显示屏（1.54寸ST7789 ）	x10
- 电池包（2000mAh）	x10
- 舵机（MG90S）	x40
- 传感器套件（手势、触摸、光敏、空气、温湿度、超声波等10多种）x4套
- 杜邦线/数据线	若干
### 工具 
- 正点原子HP15智能加热台	2台
- 正点原子DM40数字万用表	2台
- 正点原子T80/T80P智能电烙铁	2台
- 正点原子逻辑分析仪	2台
- 可调直流电源（Max 60V/5A）	1台
- 热风枪	1台
- 热胶枪	1台
- 螺丝刀	1套
- 3D打印机（拓竹 P1S+AMS）5台

---


# 技术支持 🛠️📋
- 活动现场有涂鸦的技术老师，和地瓜机器人的老师们。会在活动现场提供适当的技术支持。

:::tip
如果有是较为复杂的问题,或是活动现场没有得到支持，可以梳理好问题后在 Github 上面提 Issue 📝，我们会尽快安排人员支持。
:::

Issue Link：https://github.com/tuya/TuyaOpen/issues

### Issue 问题格式
``` shell
### 带上`【52活动】` 帮助工作人员识别活动问题
Issue 标题: 【52活动】 (bug/question/hardware): {明确清晰的问题描述}
Issue 内容：
- 开发环境：Mac/Win/Linux 💻
- 芯片平台：T5/RDK 
- 问题描述：清晰简洁的表达问题
- 问题现象：有什么规律可循，尝试过那些方法修复过了？
- 期望现象：预期的解决结果
- Log 日志：附上 Log 有助工作人员帮你分析问题 
```

---

# 常见问题
1. ESP32 怎么开发？
    - tos.py 工具能完成编译和烧写环节。代码项目选对板级config配置为 ESPxxx.config, tos.py `build` 和 `flash` 均跨平台支持。
2. TuyaOS 和 TuyaOpen 有什么区别？
    - 此文档上方有描述，按照自己需求选择，目前如果有“视频AI”，或是"商业化"需求选TuyaOS，不然强烈建议TuyaOpen。TuyaOpen生态更加开放。
3. PID 是什么？
    - 硬件关联云服务的 Product-ID。与云服务绑定的号码。
4. 授权码是什么？
    - 硬件访问云服务的安全鉴权码确保硬件安全。UUID/Key 为一组的码。注意是！TuyaOS 和 TuyaOpen 的授权码不能混用。哪怕能力和服务功能相似，授权互不兼容。
5. 我可以在 Windows 下开发码？
    - 可以的
6. 我可以在 MacOS 下开发码？
    - 内测功能，可以在Mac x86/ARM 环境下开发但是可能有未发现问题。优先建议Linun 和 Windows.



