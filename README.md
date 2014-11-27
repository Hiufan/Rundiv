# Rundiv javascript原生手机端触屏滑动、轮播插件

插件
你可以将它用在个人相册或者焦点图上面。

请注意，这是针对手机端页面设计的。（当然，也可以用在桌面端，不过不兼容旧版本的ie）

这是一个不使用jQuery小巧的框架，不到6KB。
---

#Usage
---

Rundiv only needs to follow a simple pattern. Here is an example:
```html
<div id='rundiv'>
  <div class='wrap'>
    <div></div>
    <div></div>
    <div></div>
  </div>
</div>

<!--alternative-->
<div>
  <ol id="rundivNav">  
    <li>1</li>
    <li>2</li>
    <li>3</li>
  </ol>
</div>
<!--alternative-->
```javascript
Above is the initial required structure– a series of elements wrapped in two containers. Place any content you want within the items. The containing div will need to be passed to the Rundiv function like so:
```javascript
var elem = document.getElementById('rundiv');
window.rundiv = Rundiv(elem, {
   hasNav:true,
   startSlide: 1,
   auto: 4000,
   continuous: true,
  // disableScroll: true,
  // stopPropagation: true,
  // callback: function(index, element) {},
  // transitionEnd: function(index, element) {}
});
rundiv.linkNav("rundivNav");    //the id of the ol or ul (if you use this,please make sure hasNav:true) 

});
```
I always place this at the bottom of the page, externally, to verify the page is ready.

Also Rundiv needs just a few styles added to your stylesheet:
```css
#rundiv {
  overflow: hidden;
  visibility: hidden;
  position: relative;
}
.wrap {
  overflow: hidden;
  position: relative;
}
.wrap > div {
  float:left;
  width:100%;
  position: relative;
}
```
#设置

---

 - havNav Boolean (defaule:false) - 如果你要使用导航栏 那么必须为true
 - startSlide Integer (default:1) - 从第几张开始
 - speed Integer (default:300) - 切换速度
 - auto Integer - 设置自动播放（数值为轮播速度，单位毫秒）
 - continuous Boolean (default:true) - 是否循环播放
 - disableScroll Boolean (default:false) -是否允许触摸滑动
 - stopPropagation Boolean (default:false) - 是否阻止事件冒泡
 - callback Function - 滚动开始时的回调函数
 - transitionEnd Function - 滚动结束后的回调函数

#接口

---
Rundiv也提供了一些借口供使用此插件的开发者调用：
- linkNav("id") 创建一个与你的轮播图相连的导航。（id为导航ol/ul的‘id’）
- prev() 直接滑向前一个
- next() 直接滑入下一个
- getPage() 返回当前滑动块的页码
- getNumSlides() 返回总共有多少个滑动块
- slide(index, duration) 直接滑到第index个块，所用的时间是duration(ms).

