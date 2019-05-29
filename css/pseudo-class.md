### focus-within
> 当元素本身或其后代获得焦点时，:focus-within伪类的元素就会有效

```html
<html lang="en">
<head>
  <style>
    .aaa:focus-within input {
      border: 1px solid red;
      outline: 0;
    }
  </style>
</head>
<body>
  <form class="aaa" action="" method="get">
    <input type="text" name="" id="">
    <input type="text" name="" id="">
    <input type="text" name="" id="">
    <input type="text" name="" id="">
    <input type="text" name="" id="">
  </form>
</body>
</html>
```
点击任意一个input 所有input边框都会变为红色