### flex 布局的基本概念
#### 轴线
**主轴** 由flex-direction定义
交叉轴垂直于主轴
## flex容器及容器属性
```
.container {
  display: flex; /* or inline-flex */
}
```
完成这一步之后，容器的直系子元素就会变成flex元素
#### flex-direction
主轴方向
```
.container {
  flex-direction: row | row-reverse | column | column-reverse;
}
```
#### flex-wrap
默认值 `nowrap`  
> 项目的子元素总宽度大于容器最大宽度,子元素将会缩小宽度以适应容器

```css
.container{
  flex-wrap: wrap | wrap-reverse;
}
```
- wrap
  - 子元素将换行显示
- wrap-reverse
  - 子元素向上换行

#### 简写属性 flex-flow
```css
flex-flow: <‘flex-direction’> || <‘flex-wrap’>
```
### 对齐方式
#### justify-content
可以理解为子元素在**主轴**上的对齐方式
```css
.container {
  justify-content: flex-start | flex-end | center | space-between | space-around | space-evenly;
}
```
#### align-items 
子元素在交叉轴方向对齐的对齐方式
```css
.container {
  align-items: stretch | flex-start | flex-end | center | baseline;
}
```
## flex子元素(item)属性

#### order
元素在主轴上的排序
数值越小, 排列越靠前
默认为0
 - -2 -1 0 0 0 5 
```
.item {
  order: <integer>; /* default is 0 */
}
```

#### flex-grow
拉伸因子
将flexbox剩余的宽度按照比例分配给各个子元素
```
.item {
  flex-grow: <number>; /* default 0 */
}
```
#### flex-shrink
缩放
#### flex-basis

#### align-self
子元素在交叉轴上的对齐
```
.item {
  align-self: auto | flex-start | flex-end | center | baseline | stretch;
}
```