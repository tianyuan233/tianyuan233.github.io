### ID选择器和指定id属性的属性的选择器
```css
#header {background-color: pink;}       /* 0,1,0,0 */
[id="header"] {background-color: gold;}  /*   0,0,1,0 */
```
指定id属性的 属性选择器对总特殊性贡献了 0,0,1,0

### 响应式布局 媒体查询(media quaries)的书写顺序 
```css
@media (min-width: 768px){ //>=768的设备 }
@media (min-width: 992px){ //>=992的设备 }
@media (min-width: 1200px){ //>=1200的设备 }
```
此时 如果是一个宽度为1400px的设备，即第三条生效  
反之，如果是 max-width
```css
@media (max-width: 1199px){ //<=1199的设备 }
@media (max-width: 991px){ //<=991的设备 }
@media (max-width: 767px){ //<=768的设备 }
```
### 闭合浮动
way.1 触发BFC
```
  overflow: hidden/auto/scroll;
  display: inline-block/table-cell/table/flow-root;
  position: absolute/fixed;
  float: left;

```
way.2 clearfix加伪元素
```css
.clearfix:after {
  content: "";
  display: block;
  clear: both;
}
```
```html
<div class="clearfix">...</div>
```
way.3 Bootstrap中使用的(sass)
```
// Mixin itself
@mixin clearfix() {
  &::after {
    display: block;
    content: "";
    clear: both;
  }
}

// Usage as a mixin
.element {
  @include clearfix;
}
```
### 文字溢出后显示为省略号
```css
div {
  display: block;
  text-overflow: ellipsis;
  white-space: nowrap;
  overflow: hidden;
}
```
### 伪元素插入换行符
```css
div:before {
  content: "asdadasdasd\000A asdasd";
  white-space: pre;
}
```
### 元素对鼠标点击不生效
```css
a {
  pointer-events:none;
}
```
### 无法被选中
```
user-select: none;
```