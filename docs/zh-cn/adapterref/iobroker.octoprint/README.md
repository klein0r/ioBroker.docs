---
translatedFrom: en
translatedWarning: 如果您想编辑此文档，请删除“translatedFrom”字段，否则此文档将再次自动翻译
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/zh-cn/adapterref/iobroker.octoprint/README.md
title: ioBroker.octoprint
hash: abg3z/tq5hJF+SkNY+lPHM8HD9xgDiM2TVLLIL9GiuU=
---
![商标](../../../en/adapterref/iobroker.octoprint/admin/octoprint.png)

![NPM版本](http://img.shields.io/npm/v/iobroker.octoprint.svg)
![资料下载](https://img.shields.io/npm/dm/iobroker.octoprint.svg)
![稳定](http://iobroker.live/badges/octoprint-stable.svg)
![已安装](http://iobroker.live/badges/octoprint-installed.svg)
![依赖状态](https://img.shields.io/david/klein0r/iobroker.octoprint.svg)
![已知漏洞](https://snyk.io/test/github/klein0r/ioBroker.octoprint/badge.svg)
![建立状态](http://img.shields.io/travis/klein0r/ioBroker.octoprint.svg)
![NPM](https://nodei.co/npm/iobroker.octoprint.png?downloads=true)

＃ioBroker.octoprint
将OctoPrint连接到ioBroker的适配器

＃＃ 特征
###信息
-获取版本信息
-获取打印机信息
-获取当前的打印作业信息
-获取文件列表信息

###温度
-设定工具温度
-设定床温

###命令
-打印机：连接，断开连接并返回家中
-作业：开始，取消，重新启动
-SD卡：初始化，刷新，释放
-自定义打印机命令
-系统命令
-点动X，Y和Z轴

## Changelog

### 0.0.5

* (klein0r) Switched to axios lib (replaced request - deprecated)

### 0.0.4

* (klein0r) Added missing translations
* (klein0r) Changed default port to 80

### 0.0.3

* (klein0r) Updated depencencies

### 0.0.2

* (klein0r) fixed several issues, new class based structure

### 0.0.1

* (klein0r) initial release

## License

The MIT License (MIT)

Copyright (c) 2020 Matthias Kleine <info@haus-automatisierung.com>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.