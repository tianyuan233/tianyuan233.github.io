## 介绍
sass和scss
### 变量
```scss
$base-color: #c6538c;
div {
  background-color: $base-color
}
```
### 循环
If to is used, the final number is excluded; if through is used, it's included.
```scss
@for $i from 1 through 3 {
  ul:nth-child(3n + #{$i}) {
    background-color: lighten($base-color, $i * 5%);
  }
}
```
### @mixin
define styles that can be re-used throughout your stylesheet
```scss
@mixin reset-list {
  margin: 0;
  padding: 0;
  list-style: none;
}

div {
  @include reset-list;
}
```