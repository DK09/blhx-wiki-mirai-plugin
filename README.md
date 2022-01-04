# 碧蓝航线wiki机器人插件

## 简介

基于[**mirai框架**](https://github.com/mamoe/mirai)的qq机器人插件，目前功能如下：

- 搜索[碧蓝航线wiki](https://wiki.biligame.com/blhx)上的数据
  - 舰娘基本属性、出处、语音、皮肤列表、科技点、评价、配装
  - 装备基本属性、出处
- 模拟大建

## 基本功能展示

- **查询舰娘属性**
  <img src="doc/舰娘.png" style="zoom:70%;" />
  
- **查询舰娘皮肤**
  <img src="doc/皮肤.png" style="zoom:70%;" />
  
- **查询装备属性**
  <img src="doc/装备.png" style="zoom:70%;" />
  
- **模拟大建**
  <img src="doc/大建.png" style="zoom:70%;" />

## 声明：一切开发旨在学习，请勿用于非法用途

- 本项目是完全免费且开放源代码的软件，仅供学习和娱乐用途使用
- 本项目不会通过任何方式强制收取费用，或对使用者提出物质条件
- 本项目的资料完全来自于[碧蓝航线wiki](https://wiki.biligame.com/blhx)，不保证数据的准确性和时效性
- 本项目的模拟大建功能仅供参考，不代表实际概率，~~勿上头~~
- ~~萌新的第一个kotlin、mirai项目，代码写的挺屎的~~

## 插件启用

- [安装Mirai Console](https://github.com/mamoe/mirai/blob/dev/docs/UserManual.md)

- 下载本项目最新的[jar包](https://github.com/DK09/blhx-wiki-mirai-plugin/releases)，放入Mirai-Console根目录下的plugin文件夹中

- 下载[数据文件](https://www.aliyundrive.com/s/1GcQRPKo9dj)放入Mirai-Console根目录下的data文件夹中

  ![](doc/data_path.png)

- 启动Mirai-Console，在Mirai-Console里登录

## Bot指令

此bot功能仅在群聊中开放，注意**指令用空格分开**

[] 代表该种类中的一个实例，()代表可以省略

| 群聊指令           | 描述                                             | 示例          |
|----------------| ------------------------------------------------ |-------------|
| wiki [舰娘]      | 查询舰娘基本属性                                 | wiki 拉菲     |
| wiki [舰娘] 出处   | 查询舰娘所有的出处                               | wiki 拉菲 出处  |
| wiki [舰娘] 皮肤   | 查询舰娘所有的皮肤                               | wiki 拉菲 皮肤  |
| wiki [舰娘] [语音] | 查询舰娘对应类型的语音，如果有多条则随机发送一条 | wiki 拉菲 誓约  |
| wiki [舰娘] 科技点  | 查询舰娘所提供的舰队科技                         | wiki 拉菲 科技点 |
| wiki [舰娘] 配装   | 查询舰娘的配装推荐                               | wiki 拉菲 配装  |
| wiki [舰娘] 评价   | 查询wiki大佬们对此舰娘的评价                     | wiki 拉菲 评价  |
|                |                                                  |             |
| wiki [装备]      | 查询装备的基本属性                               | wiki 533    |
| wiki [装备] 出处   | 查询装备的所有出处                               | wiki 533 出处 |
|                |                                                  |             |
| wiki 大建 (轻池)   | 模拟轻池大建                                     | wiki 大建     |
| wiki 大建列表     | 查询可以模拟大建的池子                           | wiki 大建列表  |
| wiki 大建 [池子]   | 模拟对应池子大建                                 | wiki 大建 胡滕  |

## 参数设置

$\color{red}{在修改配置文件时应确保机器人（插件）不在运行，否则机器人结束运行时会重写配置文件导致修改丢失}$

*指令自动转小写，指令、别名中的英文请使用小写字母，正式名中的空格用下划线_代替

- **指令设置**

​		位于`config/blhx-wiki/CommandConfig.yml`,对应Bot指令中的各指令名，可自行修改

- **别名设置**

  位于`config/blhx-wiki/CommandConfig.yml`，格式如下，“别名：正式名”

  ```yaml
  # 驱逐别名，指令自动转小写，别名中的英文请使用小写字母
  ALIAS_DD_MAP: 
    小加加: 萨拉托加
    彩布里: 特装型布里MKIII
    金布里: 试作型布里MKII
  ```

  正式名可以在wiki上查看，为网页网址最后的部分，如下图所示

  <img src="doc/正式名称.png" style="zoom:80%;" />

- **活动卡池设置**

  位于`data/blhx-wiki/config/active_pool.json`，格式如下
  
  ```json
  {
  	"name": "ssss",
  	"ur": [],
  	"ssr": [{
  		"name": "宝多六花",
  		"probability": 20
  	}, {
  		"name": "新条茜",
  		"probability": 20
  	}, {
  		"name": "南梦芽",
  		"probability": 20
  	}, {
  		"name": "飞鸟川千濑",
  		"probability": 5
  	}],
  	"sr": [{
  		"name": "奈美子",
  		"probability": 25
  	}, {
  		"name": "莲SSSS",
  		"probability": 25
  	}],
  	"r": []
  }
  ```
  
  最开始的`name`为卡池名称，`ur、ssr、sr、r`为各稀有度的舰娘列表，其中`name`为舰娘名称，`probability`为概率*10
  
  ~~目前还没加入概率校验，等之后在摸吧~~



## 常见问题

- **大建列表乱码**

  将`data/blhx-wiki/config/active_pool.json`文件改为GBK格式即可

~~如果觉得还不错就点个star吧~~
