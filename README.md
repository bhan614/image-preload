# 图片预加载

> preload create by jquery

## 无序预加载
浏览前加载所有图片，并用提示显示进度或loading，使用jquery封装插件。
1. 图片预加载，翻页展示。
2. qq表情预加载，打开展示。

### 核心代码
``` bash
PreLoad.prototype._unordered = function(){   //无序加载
  var imgs = this.imgs,
      opts = this.opts,
      count = 0,
      len = imgs.length;
  $.each(imgs, function(i, src) {
    if (typeof src != 'string') {
      return;
    }
    var imgObj = new Image();
    $(imgObj).on('load error', function() {
      opts.each && opts.each(count);
      if (count >= len - 1) {
        opts.all && opts.all();
      }
      count++;
    });
    imgObj.src = src;
  });
};
```
