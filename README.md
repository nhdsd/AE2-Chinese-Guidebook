Due to the purpose of this project, the readme will be written in Chinese (Simplified).

鉴于本项目的目的，readme文件将使用简体中文书写。

---

# AE2 Chinese Guidebook

**本项目并未完成翻译！已经完成翻译的部分请见文末列表。文之所译，未必悉准。如有纰漏，敬请[指正](https://github.com/nhdsd/AE2-Chinese-Guidebook/issues/new?template=Blank+issue)。**

## 关于本项目
本项目旨在为 Minecraft 模组[**应用能源2**(Applied Energistics 2)](https://github.com/AppliedEnergistics/Applied-Energistics-2)(以下简称AE2)的游戏内指南提供简体中文翻译。相关内容适用于1.20.1版本的模组。

## 使用本项目
由于 AE2 的游戏内指南未采用语言文件的形式，因此无法使用资源包进行替换，需要直接替换模组中的文件。

**请注意：这样做之后游戏内的指南将永远以简体中文显示，即使你切换到英语。请注意备份原文件。**

1. 在模组安装目录下用任意压缩软件将 AE2 模组文件解压。
2. 在解压得到的文件夹中，进入`.\assets\ae2\ae2guide`目录。
3. 将目录下的所有文件替换为本项目中的文件。
4. 回到解压得到的文件夹的根目录，运行命令提示符(cmd)，输入`jar cvf <jarName> *`。参数`<jarName>`应当替换成合适的名称(带后缀名`.jar`)。
5. 把原模组文件移除，把得到的新文件放入模组安装目录下。

## Q & A

Q1 为何不使用 Crowdin 翻译相关内容？

A1 因为 Crowdin 上没有。 :-(

Q2 我能够使用此项目中的内容用于教学等目的吗？

A2 当然！只要你遵循本项目的开源许可证。但是，你可能同时需要遵守原项目的[开源许可证](https://github.com/AppliedEnergistics/Applied-Energistics-2?tab=License-1-ov-file#readme)。

## 完成情况

### 完全完成
* `tips-and-tricks.md`
* `index.md`
* `getting-started.md`
* `ae2-mechanics\`
  * `ae2-mechanics-index.md`
  * `autocrafting.md`
  * `bytes-and-types.md`
  * `cable-subparts.md`
  * `certus-growth.md`
  * `channels.md`
  * `devices.md`
  * `energy.md`
  * `import-export-storage.md`
  * `me-network-connections.md`
  * `meteorites.md`
  * `p2p-tunnels.md`
  * `quantum-bridge.md`

### 部分完成

### 计划中
**部分完成**部分的内容默认计入**计划中**部分。
* `ae2-mechanics\`
  * `import-export-storage.md`