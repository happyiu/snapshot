# ympic

## 介绍

一个简单的 页面快照 demo

## 原理

基于 canvas调用API 绘制页面 ，然后调用API将canvas的图片转化

```html
<img id="target" src="./logo.jpg">
```

```js
const target = document.getElementById('target')

// 新建 canvas 画布
const canvas = document.createElement('canvas')
canvas.width = 100
canvas.height = 100
const ctx = canvas.getContext("2d")

// 将 canvas 画布 导出
const exportNewImage = (canvas)=>{
  // js插创建一个 img标签
  const exportImage = document.createElement('img')
  // 将画布绘制的内容转化为 src
  exportImage.src = canvas.toDataURL()
  // 将图片插入页面
  document.body.appendChild(exportImage)
}

// 绘制阶段，待图片加载完毕后绘制画布
target.onload = () => {
  // 将图片内容汇入画布
  ctx.drawImage(target,0,0,100,100)
  // 将 canvas画布 导出为 新的图片
  exportNewImage(canvas)
}
```

## demo
demo 主要 使用了 html2canvas 快速选择要快照的区域，然后导出图片


## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
