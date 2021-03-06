---
translatedFrom: en
translatedWarning: 如果您想编辑此文档，请删除“translatedFrom”字段，否则此文档将再次自动翻译
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/zh-cn/adapterref/iobroker.echarts/README.md
title: ioBroker.echarts
hash: JyOvcim9n28Qm0LRcmvtB4ihyR6nR5gEN6Q9Wd9/vKQ=
---
![商标](../../../en/adapterref/iobroker.echarts/admin/echarts.png)

![NPM版本](http://img.shields.io/npm/v/iobroker.echarts.svg)
![资料下载](https://img.shields.io/npm/dm/iobroker.echarts.svg)
![依赖状态](https://img.shields.io/david/ioBroker/iobroker.echarts.svg)
![已知漏洞](https://snyk.io/test/github/ioBroker/ioBroker.echarts/badge.svg)
![NPM](https://nodei.co/npm/iobroker.echarts.png?downloads=true)

＃ioBroker.echarts
## IoBroker的echarts适配器
在ioBroker中构建有用的图表：

![屏幕截图](../../../en/adapterref/iobroker.echarts/img/screenshot1.png)

##用法
重新启动后，在admin中添加选项卡：![管理员](../../../en/adapterref/iobroker.echarts/img/admin.png)

###服务器端渲染
您可以在服务器上呈现预设并将其作为base64 URL获得，或将其保存在ioBroker DB中的磁盘上：

```
sendTo('echarts.0', {
    preset:   'echarts.0.myPreset', // the only mandatory attribute

    renderer: 'svg',                // svg | png | jpg | pdf, default: svg

    width: 1024,                    // default 1024
    height: 300,                    // default 300
    background: '#000000',          // Background color
    theme: 'light',                 // Theme type: 'light', 'dark'

    title: 'ioBroker Chart',        // Title of PDF document
    quality: 0.8,                   // quality of JPG
    compressionLevel: 3,            // Compression level of PNG
    filters: 8,                     // Filters of PNG (Bit combination https://github.com/Automattic/node-canvas/blob/master/types/index.d.ts#L10)

    fileOnDisk: '',                 // Path on disk to save the file
    fileName: '',                   // Path in ioBroker DB to save the files on 'echarts.0',
}, result => {
    if (result.error) {
        console.error(result.error);
    } else {
        console.log(result.data);
    }
});
```

##开发人员手册
您可以使用以下命令在本地调试视图图表：

-光盘iobroker.echarts / src-chart
-npm运行开始
-浏览器：http：// localhost：8081 / adapter / echarts / tab.html？dev = true

＃＃ 去做
-可见部件（按钮）
-材料小部件
-在文件夹或其附近显示枚举图标
-拖放预设以重新排序

<！-下一个版本的占位符（在该行的开头）：

### __进展中__->

## Changelog
### 0.3.4 (2020-11-08)
* (bluefox) Corrected server-side rendering of PNG 

### 0.3.1 (2020-10-31)
* (bluefox) Added the color of export button 
* (bluefox) The interpolated values are shown now
* (bluefox) Server-side rendering is implemented

### 0.2.1 (2020-10-25)
* (bluefox) GUI fixes

### 0.2.0 (2020-10-22)
* (bluefox) Implemented the grouping by category.

### 0.1.2 (2020-10-21)
* (bluefox) Added support of multiple charts

### 0.1.1 (2020-10-21)
* (bluefox) initial release

## License
MIT License

Copyright (c) 2019-2020 bluefox <dogafox@gmail.com>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.