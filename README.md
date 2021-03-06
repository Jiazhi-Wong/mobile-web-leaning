# 移动web的学习

## 第一课总结

1. 不设置viewport的属性，在手机端默认像素为980px（宽度为手机的点point），此时像素比为手机设置的像素比，但是css中的1px是单个的分布在980px里，类似pc端，一个css的像素对应一个设备的物理像素，这时候字很小。
2. 当设置的viewport的initial-scale值，显示会有所不同。当initial-scale为1时，在手机端显示的像素为设备的点point（一个点包含像素比个物理像素），此时css中的1px是单个的分布在这些点point里，一个css的像素对应像素比（devicePixelRatio的值）个设备的物理像素。
3. 当用户把页面放大一倍，或者将initial-scale值设置成2.0，那么css中1px所代表的物理像素也会增加一倍，设备显示的像素会减少一倍；反之把页面缩小一倍，或者将initial-scale值设置成0.5，css中1px所代表的物理像素也会减少一倍，设备显示的像素会增加一倍。

### 参考资料
* [iPhone分辨率指南](http://images.shejidaren.com/wp-content/uploads/2014/09/iphone-Resolutions-guide.png)
* [移动前端开发之viewport的深入理解](http://www.cnblogs.com/2050/p/3877280.html)

## 第二课总结

1. 直接使用像素值为元素设置宽高，在不同移动设备下分辨率不同，产生的布局就不同
2. 使用百分比为元素设置宽高，相对于父级元素来设置，计算麻烦，耦合度高
3. 使用em单位为元素设置宽高，相对于本元素的字体大小(`font-size`)来设置，不够自由，耦合度高
4. 使用rem单位为元素设置宽高，相对于`<html>`的字体大小来设置，方便自由，耦合度低
5. 在不同分辨率的设备下，假如不对`<html>`的字体大小按比例进行改变，那么计算出来的宽高会保持不变，布局会产生差异，所以需要js**动态设置`<html>`字体的大小**
```
// 动态设置html字体的大小
var html = document.documentElement;
var iWidth = html.clientWidth;
	
html.style.fontSize = iWidth / 16 + "px";
```
