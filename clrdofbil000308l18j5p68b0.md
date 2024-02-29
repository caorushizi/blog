---
title: "HTML5 canvas 在画布中画出一个时钟"
datePublished: Sun Jan 14 2024 15:54:14 GMT+0000 (Coordinated Universal Time)
cuid: clrdofbil000308l18j5p68b0
slug: html5-canvas-1
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1709200509314/fbf63d12-44ad-4e9f-8dab-47b900741532.webp
tags: html5

---

在画布中画出一个时钟

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


    window.onload = function () {
        var canvas = document.getElementById('myCanvas');
        var context = canvas.getContext('2d');

        canvas.width = 1152;
        canvas.height = 768;

        function toDraw() {
            var x = 200;
            var y = 200;
            var r = 150;

            context.clearRect(0, 0, canvas.width, canvas.height);

            var oDate = new Date();
            var oHours = oDate.getHours();
            var oMin = oDate.getMinutes();
            var oSen = oDate.getSeconds();

            var oHoursValue = (-90 + oHours * 30 + oMin / 2) * Math.PI / 180;
            var oMinValue = (-90 + oMin * 6) * Math.PI / 180;
            var oSenValue = (-90 + oSen * 6) * Math.PI / 180;


            context.beginPath();
            for (var i = 0; i < 60; i++) {
                context.moveTo(x, y);
                context.arc(x, y, r, 6 * i * Math.PI / 180, 6 * (i + 1) * Math.PI / 180, false);
            }
            context.closePath();
            context.stroke();

            context.fillStyle = "white";
            context.beginPath();
            context.moveTo(x, y);
            context.arc(x, y, r * 19 / 20, 0, 360 * Math.PI / 180, false);
            context.closePath();
            context.fill();

            context.lineWidth = 3;
            context.beginPath();
            for (var i = 0; i < 12; i++) {
                context.moveTo(x, y);
                context.arc(x, y, r, 30 * i * Math.PI / 180, 30 * (i + 1) * Math.PI / 180, false);
            }
            context.closePath();
            context.stroke();

            context.fillStyle = "white";
            context.beginPath();
            context.moveTo(x, y);
            context.arc(x, y, r * 18 / 20, 0, 360 * Math.PI / 180, false);
            context.closePath();
            context.fill();

            context.lineWidth = 5;
            context.beginPath();
            context.moveTo(x, y);
            context.arc(x, y, r * 10 / 20, oHoursValue, oHoursValue, false);
            context.closePath();
            context.stroke();

            context.lineWidth = 3;
            context.beginPath();
            context.moveTo(x, y);
            context.arc(x, y, r * 14 / 20, oMinValue, oMinValue, false);
            context.closePath();
            context.stroke();

            context.lineWidth = 1;
            context.beginPath();
            context.moveTo(x, y);
            context.arc(x, y, r * 19 / 20, oSenValue, oSenValue, false);
            context.closePath();
            context.stroke();

        }

        setInterval(toDraw,500);
        toDraw();

    }

</script>
</body>
</html>
```