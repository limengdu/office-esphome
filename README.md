# 🏠 Maker Faire 智能家居演示项目

<p align="center">
  <img src="https://img.shields.io/badge/Platform-ESPHome-blue?style=for-the-badge&logo=esphome" />
  <img src="https://img.shields.io/badge/Integration-Home%20Assistant-41BDF5?style=for-the-badge&logo=home-assistant" />
  <img src="https://img.shields.io/badge/Hardware-Seeed%20Studio-green?style=for-the-badge" />
</p>

> 🎪 **一个为 Maker Faire 打造的完整智能家居演示系统！**
> 
> 使用 Seeed Studio XIAO ESP32 系列开发板 + ESPHome + Home Assistant 构建的全功能智能家居解决方案。

---

## ✨ 项目亮点

- 🎯 **即插即用** - 所有配置开箱可用，轻松烧录
- 🌈 **功能丰富** - 涵盖智能照明、环境监测、健康监护等多个场景
- 📊 **可视化仪表盘** - 精美的电子墨水屏数据中心 + Home Assistant 控制面板
- 🌐 **双语支持** - 提供中英文 Dashboard 配置
- 🔧 **高度可定制** - 模块化设计，方便二次开发

---

## 🎁 设备清单

| 设备 | 芯片 | 功能 | 文件 |
|------|------|------|------|
| 📷 **XIAO ESP32-S3 Sense 摄像头** | ESP32-S3 | 卧室实时监控 | `xiao-esp32s3-camera.yaml` |
| 🛏️ **MR60BHA2 毫米波雷达套件** | ESP32-C6 | 人体存在检测、心率、呼吸监测 | `mr60bha2.yaml` |
| 🔘 **Seeed IoT 按钮** | ESP32-C6 | 三功能无线按钮（单击/双击/长按） | `seeed-iot-button.yaml` |
| 💨 **XIAO 气体传感器** | ESP32-C3 | VOC、CO、NO₂、乙醇检测 | `xiao-esp32-c3-gas-sensor.yaml` |
| 🌈 **XIAO LED 灯带控制器** | ESP32-C3 | WS2812 可寻址灯带（48颗灯珠） | `xiao-esp32-c3-led-strip.yaml` |
| 🎵 **XIAO MP3 播放器** | ESP32-C3 | WT2605C 模块，支持 SD 卡播放 | `xiao-esp32-c3-mp3.yaml` |
| 🌀 **XIAO 智能风扇** | ESP32-C6 | PWM 调速电机控制 | `xiao-esp32-c6-fan.yaml` |
| 💡 **XIAO LED 发光按钮** | ESP32-C6 | 3路带灯按钮控制 | `xiao-esp32-c6-led-button.yaml` |
| 🌱 **XIAO 土壤湿度传感器** | ESP32-C6 | 植物浇水提醒，支持校准 | `xiao-soil-moisture.yaml` |
| 📺 **reTerminal E1002** | ESP32-S3 | 7.3寸彩色电子墨水屏仪表盘 | `reterminal-e1002.yaml` |

---

## 🚀 快速开始

### 📋 前置要求

- ✅ [ESPHome](https://esphome.io/) 已安装（推荐使用 Home Assistant 插件版）
- ✅ [Home Assistant](https://www.home-assistant.io/) 运行中
- ✅ WiFi 网络环境
- ✅ 上述硬件设备

### 🔧 安装步骤

#### 1️⃣ 克隆项目

```bash
git clone https://github.com/your-repo/maker_faire_demo.git
cd maker_faire_demo
```

#### 2️⃣ 创建 WiFi 配置文件

在项目目录下创建 `secrets.yaml` 文件：

```yaml
# secrets.yaml
wifi_ssid: "你的WiFi名称"
wifi_password: "你的WiFi密码"
```

#### 3️⃣ 编译并烧录

使用 ESPHome 命令行工具：

```bash
# 编译固件
esphome compile xiao-esp32-c3-led-strip.yaml

# 烧录到设备（首次需要 USB 连接）
esphome upload xiao-esp32-c3-led-strip.yaml

# 或者一步到位：运行 = 编译 + 烧录 + 日志
esphome run xiao-esp32-c3-led-strip.yaml
```

#### 4️⃣ 添加到 Home Assistant

设备上线后，Home Assistant 会自动发现新设备。前往：
> **设置** → **设备与服务** → **集成** → 点击 **配置** ESPHome 设备

---

## 📱 设备详细说明

### 📷 XIAO ESP32-S3 Sense 摄像头

超紧凑的 WiFi 摄像头解决方案！

```yaml
# 主要特性
- 支持 PSRAM（OCTAL 模式，80MHz）
- 自动画面翻转
- 实时视频流推送到 Home Assistant
```

**🔌 接线**：无需额外接线，使用板载 OV2640 摄像头

---

### 🛏️ MR60BHA2 毫米波雷达

60GHz 毫米波雷达，非接触式健康监测黑科技！

```yaml
# 检测能力
- 👤 人体存在检测
- 📏 目标距离测量
- ❤️ 实时心率监测
- 🌬️ 实时呼吸频率监测
- 💡 环境光照度（BH1750）
- 🌈 RGB 指示灯
```

**🔌 接线**：
| MR60BHA2 | ESP32-C6 |
|----------|----------|
| RX | GPIO17 |
| TX | GPIO16 |
| SDA | GPIO22 |
| SCL | GPIO23 |

---

### 🔘 Seeed IoT 按钮

一颗按钮，三种玩法！RGB 灯光反馈超酷炫！

```yaml
# 操作方式
- 单击：触发开关1 + 闪烁效果
- 双击：触发开关2 + 闪烁效果
- 长按(1-2秒)：触发开关3 + 彩虹效果
```

**💡 RGB 灯效**：
- Blink（闪烁）
- Rainbow（彩虹）
- Subtle Flicker（微光闪烁）
- Random Color（随机颜色）

---

### 💨 XIAO 气体传感器

守护你的空气质量！支持多种气体检测。

```yaml
# 检测指标
- 🧪 VOC（挥发性有机化合物）
- 💀 CO（一氧化碳）
- ⚠️ NO₂（二氧化氮）
- 🍺 Ethanol（乙醇）
```

**🔌 接线**：
| Grove 气体传感器 | ESP32-C3 |
|-----------------|----------|
| SDA | GPIO6 |
| SCL | GPIO7 |

---

### 🌈 XIAO LED 灯带控制器

48颗 WS2812 灯珠，打造梦幻氛围灯！

```yaml
# 内置灯效（一键切换）
🔴 Pulse（脉冲）
🔵 Strobe（频闪）
🟣 Strobe Red and Blue（红蓝警灯）
🟢 Random（随机颜色）
🟡 Slow Random Transition（慢速渐变）
🟠 Flicker（烛火效果）
🌈 Rainbow / Fast Rainbow（彩虹）
🎨 Color Wipe（颜色擦除）
✨ Twinkle / Random Twinkle（星光闪烁）
🎆 Fireworks（烟花）
🔄 Automation RGB Cycle（RGB 循环）
```

**🔌 接线**：LED 数据线接 GPIO2

---

### 🎵 XIAO MP3 播放器

基于 WT2605C 模块的智能音乐播放器！

```yaml
# 功能特性
▶️ 播放/暂停/停止
⏮️⏭️ 上一曲/下一曲
🔊 音量调节（0-31级）
🔁 播放模式：顺序/单曲循环/文件夹循环/随机/单次

# Home Assistant 服务
- play_track：播放指定曲目
- play_file：播放指定文件名
- set_volume：设置音量
- send_command：发送自定义 AT 命令
```

**🔌 接线**：
| WT2605C | ESP32-C3 |
|---------|----------|
| RX | GPIO21 |
| TX | GPIO20 |

**📁 SD 卡格式**：歌曲命名为 `0001.mp3`, `0002.mp3`...

---

### 🌀 XIAO 智能风扇

PWM 调速电机控制，正反转自如！

```yaml
# 控制功能
🔄 正转（开启）
🔃 反转（关闭）
⏹️ 停止
📊 速度滑块调节（0-100%）
```

**🔌 接线**：
| 电机驱动 | ESP32-C6 |
|---------|----------|
| IA（正转）| GPIO1 |
| IB（反转）| GPIO0 |

---

### 💡 XIAO LED 发光按钮

3路带灯按钮，按下即亮，反馈清晰！

```yaml
# 特性
- 开机自动亮灯
- 按下时闪烁2次反馈
- 每个按钮独立控制
- 可绑定 Home Assistant 自动化
```

**🔌 接线**：
| 按钮 | LED(SIG1) | BTN(SIG2) |
|------|-----------|-----------|
| 按钮1 | GPIO0 | GPIO1 |
| 按钮2 | GPIO19 | GPIO20 |
| 按钮3 | GPIO2 | GPIO21 |

---

### 🌱 XIAO 土壤湿度传感器

智能植物保姆，再也不怕忘记浇水！

```yaml
# 特性
- 🔴 红灯：土壤干燥，需要浇水
- 🟡 黄灯：土壤偏干，可以浇水
- 🟢 绿灯：湿度正常

# 操作
- 单击按钮：检测一次并闪灯提示
- 连续3次按钮：进入校准模式
```

**📊 校准流程**：
1. 红灯闪烁 10 秒 → 将传感器放入干燥土壤
2. 绿灯闪烁 10 秒 → 将传感器放入湿润土壤
3. 绿灯快闪 = 校准成功 ✅ / 红灯快闪 = 校准失败 ❌

---

### 📺 reTerminal E1002 电子墨水屏

7.3 寸彩色电子墨水屏，打造智能家居数据中心！

```yaml
# 显示页面
📄 Page 1：传感器数据概览
  - 卧室状态（光照、距离、心率、呼吸）
  - 阳台植物（土壤湿度、电池电量）
  - 全屋用电（电压、功率、电流、总能耗）

📄 Page 2：开关控制
  - MP3 播放控制（播放/暂停、上一曲、下一曲）
  - LED 灯带控制
  - 风扇控制
  - 客厅空气质量（CO、NO₂、乙醇、VOC）

📄 Page 3：传感器数据（黄色主题）
  - 卧室状态卡片
  - 阳台植物卡片
  - 全屋用电大卡片
  - 设备功耗卡片
```

**🎛️ 按钮操作**：
| 按钮 | 功能 |
|------|------|
| 绿色键 | 刷新屏幕（双声蜂鸣反馈）|
| 右侧白键 | 下一页 |
| 左侧白键 | 上一页 |

---

## 🎨 Home Assistant 仪表盘

项目包含两个精心设计的 Dashboard 配置：

| 文件 | 语言 | 说明 |
|------|------|------|
| `chinese-dashboard.yaml` | 🇨🇳 中文 | 完整中文界面 |
| `english-dashboard.yaml` | 🇺🇸 英文 | 完整英文界面 |

### 📥 导入方法

1. 打开 Home Assistant
2. 进入 **设置** → **仪表盘**
3. 点击 **添加仪表盘**
4. 选择 **从 YAML 创建**
5. 复制粘贴对应文件内容

---

## 🔗 购买链接

| 产品 | 链接 |
|------|------|
| XIAO ESP32-C3 | [Seeed Studio](https://www.seeedstudio.com/Seeed-XIAO-ESP32C3-p-5431.html) |
| XIAO ESP32-C6 | [Seeed Studio](https://www.seeedstudio.com/Seeed-Studio-XIAO-ESP32C6-p-5884.html) |
| XIAO ESP32-S3 Sense | [Seeed Studio](https://www.seeedstudio.com/XIAO-ESP32S3-Sense-p-5639.html) |
| MR60BHA2 Kit | [Seeed Studio](https://www.seeedstudio.com/60GHz-mmWave-Radar-Sensor-Breathing-and-Heartbeat-Module-Lite-p-5860.html) |
| reTerminal E1002 | [Seeed Studio](https://www.seeedstudio.com/) |
| Grove 气体传感器 V2 | [Seeed Studio](https://www.seeedstudio.com/Grove-Multichannel-Gas-Sensor-v2-p-4569.html) |

---

## 📚 参考资源

- 📖 [ESPHome 官方文档](https://esphome.io/)
- 🏠 [Home Assistant 官方文档](https://www.home-assistant.io/docs/)
- 🌱 [Seeed Studio Wiki](https://wiki.seeedstudio.com/)
- 🎯 [MR60BHA2 ESPHome 组件](https://github.com/limengdu/MR60BHA2_ESPHome_external_components)

---

## 🤝 贡献

欢迎提交 Issue 和 Pull Request！

如果这个项目对你有帮助，请给个 ⭐ Star 支持一下！

---

## 📄 许可证

MIT License - 随心使用，注明出处即可 😊

---

<p align="center">
  <b>🎪 Made with ❤️ for Maker Faire</b>
  <br>
  <i>让智能家居触手可及！</i>
</p>

