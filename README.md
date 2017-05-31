# 图片预加载

> preload create by jquery

## 无序预加载
浏览前加载所有图片，并用百分比显示进度，使用jquery封装插件。

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
