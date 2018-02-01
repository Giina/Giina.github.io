---
title: html5简单视频播放功能实现
lang: zh
date: 2018-02-01 16:50:32
tags:
category: "工作"
---
### 手机版功能说明
1. 显示封面，点击播放（不要预先加载）
2. 无下载按钮
3. 可以全屏+控制播放进度

### 技能点
1. html 5 <video>标签
2. 去掉video的下载按钮
3. poster字段设置封面
4. preload字段设置不要预加载

### 问题
1. 搜狗浏览器的播放器控制条跟其他webkit的浏览器不一样

```
<video class="cover" src="http://www.w3school.com.cn/i/movie.ogg" poster="http://www.w3school.com.cn/i/eg_tulip.jpg" controls preload="none">
啊！显示不了...
</video>

<style>
video::-internal-media-controls-download-button {
  display:none;
}
video::-webkit-media-controls-enclosure {
  overflow:hidden;
}
video::-webkit-media-controls-panel {
  width: calc(100% + 6rem);
}
</style>
```

<video class="cover" src="http://www.w3school.com.cn/i/movie.ogg" poster="http://www.w3school.com.cn/i/eg_tulip.jpg" controls preload="none">
啊！显示不了...
</video>

<style>
video::-internal-media-controls-download-button {
  display:none;
}
video::-webkit-media-controls-enclosure {
  overflow:hidden;
}
video::-webkit-media-controls-panel {
  width: calc(100% + 60px);
}
</style>