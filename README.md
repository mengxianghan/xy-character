# character

一个可以将字符串转换成 svg 图片的插件，支持田字格、方格、拼音+田字格、拼音+方格、拼音+汉字，解决多端兼容问题。

## 安装

```shell
# 使用 npm
npm install --save-dev xy-character
```

## 使用

> 为保证最终效果，拼音字体建议使用 `dist/pinyin.ttf`

### 拼音

```js
import { Pinyin } from 'xy-character'
const pinyin = new Pinyin()

pinyin.load(['pinyin.ttf', 'kaiti.woff']).then(() => {
    const svg = pinyin.getSVG([
        { pinyin: 'shì', chinese: '示' },
        { pinyin: 'lì', chinese: '例' },
    ])
    document.body.appendChild(svg)
})
```

<img src="http://cdn.xuanyunet.com/images/pinyin_text.png" height="60">

### 拼音田字

```js
import { PinyinTianzi } from 'xy-character'
const pinyinTianzi = new PinyinTianzi()

// 带汉字
pinyinTianzi.load(['pinyin.ttf', 'kaiti.woff']).then(() => {
    const svg = pinyinTianzi.getSVG([
        { pinyin: 'shì', chinese: '示' },
        { pinyin: 'lì', chinese: '例' },
    ])
    document.body.appendChild(svg)
})

// 不带汉字
pinyinTianzi.load(['pinyin.ttf', 'kaiti.woff']).then(() => {
    const svg = pinyinTianzi.getSVG([{ pinyin: 'shì' }, { pinyin: 'lì' }])
    document.body.appendChild(svg)
})
```

#### 输出

<img src="http://cdn.xuanyunet.com/images/pinyin_tianzi.png" height="80">

### 拼音方格

```js
import { PinyinTianzi } from 'xy-character'
const pinyinTianzi = new PinyinTianzi()

// 带汉字
pinyinTianzi.load(['pinyin.ttf', 'kaiti.woff']).then(() => {
    const svg = pinyinTianzi.getSVG(
        [
            { pinyin: 'shì', chinese: '示' },
            { pinyin: 'lì', chinese: '例' },
        ],
        { gridType: 2 }
    )
    document.body.appendChild(svg)
})

// 不带汉字
pinyinTianzi.load(['pinyin.ttf', 'kaiti.woff']).then(() => {
    const svg = pinyinTianzi.getSVG([{ pinyin: 'shì' }, { pinyin: 'lì' }], { gridType: 2 })
    document.body.appendChild(svg)
})
```

#### 输出

<img src="http://cdn.xuanyunet.com/images/pinyin_square.png" height="80">

### 田字格

```js
import { Tianzi } from 'xy-character'
const tianzi = new Tianzi()

// 带汉字
tianzi.load('kaiti.woff').then(() => {
    const svg = tianzi.getSVG('示例')
    document.body.appendChild(svg)
})

// 不带汉字
tianzi.load(['kaiti.woff']).then(() => {
    const svg = tianzi.getSVG(2)
    document.body.appendChild(svg)
})
```

#### 输出

<img src="http://cdn.xuanyunet.com/images/tianzi.png" height="60">

### 方格

```js
import { Tianzi } from 'xy-character'
const tianzi = new Tianzi()

// 带汉字
tianzi.load('kaiti.woff').then(() => {
    const svg = tianzi.getSVG('示例', { gridType: 2 })
    document.body.appendChild(svg)
})

// 不带汉字
tianzi.load(['kaiti.woff']).then(() => {
    const svg = tianzi.getSVG(2, { gridType: 2 })
    document.body.appendChild(svg)
})
```

#### 输出

<img src="http://cdn.xuanyunet.com/images/square.png" height="60">

## 类

### Character.Pinyin

#### load(url: string[], callback: (err, data?) => {}, options: object): Promise

加载字体文件。异步方法，返回 `Promise`，使用 `getSVG` 方法前调用

#### getSVG(text: Array<{pinyin:string, chinese?:string}>, options?: { attrs?: object }): SVGElement

获取生成的 `svg` 节点

### Character.PinyinTianzi

#### load(url: string[], callback: (err, data?) => {}, options: object): Promise

加载字体文件。异步方法，返回 `Promise`，使用 `getSVG` 方法前调用

#### getSVG(text: Array<{pinyin:string, chinese?:string}>, options?: { attrs?: object, gridType: 1｜2 }): SVGElement

获取生成的 `svg` 节点

### Character.Tianzi

#### load(url: string, callback: (err, data?) => {}, options: object): Promise

加载字体文件。异步方法，返回 `Promise`，使用 `getSVG` 方法前调用

#### getSVG(text: Array<{pinyin:string, chinese?:string}>, options?: { attrs?: object, gridType: 1｜2 }): SVGElement

获取生成的 `svg` 节点

## 依赖
- [opentype.js](https://github.com/opentypejs/opentype.js)

## 学习交流
微信号：meng_xianghan

或使用微信扫以下二维码加为好友

<img src="http://cdn.xuanyunet.com/images/wechat-qrcode.jpg" width="200" />

## 感谢

<img src="https://resources.jetbrains.com/storage/products/company/brand/logos/jb_beam.svg" alt="JetBrains Logo (Main) logo." height="100">
