---
title: "HTML5 canvas 两个小程序"
datePublished: Sun Jan 14 2024 15:53:42 GMT+0000 (Coordinated Universal Time)
cuid: clrdoem4u000b09l7enj7843z
slug: html5-canvas
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1709200522851/c945ce94-c76c-49b9-b500-06f9a1d6a0f9.webp
tags: html5

---

用鼠标在canvas画布上画出图像

```xml
<!DOCTYPE html>
<html lang="zh">
<head>
    <meta charset="UTF-8">
    <title>画图</title>
</head>
<body>
<canvas id="myCanvas" style="border: 1px #000 solid;">
    你的浏览器不支持canvas
</canvas>
<script type="text/javascript">
    var canvas = document.getElementById('myCanvas');
    var context = canvas.getContext('2d');
    canvas.width = 1152;
    canvas.height = 768;
    canvas.onmousedown = function (ev) {
        var ev = ev || window.event;
        context.moveTo(ev.clientX - canvas.offsetLeft, ev.clientY - canvas.offsetTop);
        document.onmousemove = function (ev) {
            var ev = ev || window.event;
            context.lineTo(ev.clientX - canvas.offsetLeft, ev.clientY - canvas.offsetTop);
            context.stroke();
        }
        document.onmouseup = function () {
            document.onmousemove = null;
            document.onmouseup = null;
        }
    }


</script>
</body>
</html>
```

画布上矩形的移动

```xml
<!DOCTYPE html>
<html lang="zh">
<head>
    <meta charset="UTF-8">
    <title>画图</title>
</head>
<body>
<canvas id="myCanvas" style="border: 1px #000 solid;">
    你的浏览器不支持canvas
</canvas>


<script type="text/javascript">

    var canvas = document.getElementById('myCanvas');
    var context = canvas.getContext('2d');

    canvas.width = 1152;
    canvas.height = 768;
    
    var num = 0;
    context.fillRect(0, 0, 100, 100);
    setInterval(function () {
        num++;
        context.clearRect(0, 0, canvas.width, canvas.height);
        context.fillRect(num, num, 100, 100);

    }, 30)

</script>
</body>
</html>
```