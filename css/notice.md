### ID选择器和指定id属性的属性的选择器
```css
#header {background-color: pink;}       /* 0,1,0,0 */
[id="header"] {background-color: gold;}  /*   0,0,1,0 */
```
指定id属性的 属性选择器对总特殊性贡献了 0,0,1,0

### 媒体查询(media quaries)的书写顺序
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