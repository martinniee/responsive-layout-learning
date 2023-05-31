> - 课程：[六个案例学会响应式布局-慕课网](https://www.imooc.com/learn/1285)
> - 作者：[大谷](https://www.imooc.com/t/3414982)
> - 时长： 2小时41分 
> - 计划：3天
> - 周期：2023/5/30 ~ ?????
> - 资源：



## 前言

响应式布局的需求（课程需求）：

- 解决页面布局在不同设备的显示情况
- 解决传统布局仅使用 float + position的局面，使用flex
- 使用em单位代替传统的px,%
- 掌握响应式布局，弹性布局等常用布局

课程安排

- CSS中媒体查询的作用和使用方法
- flex弹性盒子的用法
- rem的作用和使用方法
- 响应式布局、弹性布局等六个课程案例



## 媒体查询

概念：为不同尺寸的屏幕设定不同的CSS样式

媒体查询的示例代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>媒体查询</title>
    <style>
        #div0{
            width: 100px;
            height: 200px;
        }
        /* 媒体查询 */
        /* 表示在屏幕尺寸 在 100px ~ 199px 之间生效 */
        @media screen and (min-device-width:100px) and (max-device-width:199px){
            #div0{
                background-color: green;
            }
        } 
        /* 表示在屏幕尺寸 在 200px ~ 300px 之间生效 */
        @media screen and (min-device-width:200px) and (max-device-width:300px){
            #div0{
                background-color: red;
            }
        } 
        /* 表示在屏幕尺寸 在 301px ~ 500px 之间生效 */
        @media screen and (min-device-width:301px) and (max-device-width:500px){
            #div0{
                background-color: blue;
            }
        } 
    </style>
</head>
<body>
    <div id="div0"></div>
</body>
</html>
```

### 常用参数

浏览器与设备

1. 浏览器：width, height
2. 设备：device-width, device-height



案例1：根据浏览器尺寸不同，决定元素显示颜色

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>媒体查询</title>
    <style>
        #div0{
            width: 200px;
            height: 200px;
        }
        /* 表示在浏览器屏幕尺寸 在 500px ~ 700px 之间生效 */
        @media screen and (min-width:500px) and (max-width:700px){
            #div0{
                background-color: red;
            }
        } 
        /* 表示在浏览器屏幕尺寸 > 701px 生效 */
        @media screen and (min-width:701px){
            #div0{
                background-color: blue;
            }
        } 
       
    </style>
</head>
<body>
    <div id="div0"></div>
</body>
</html>
```

案例2：根据浏览器宽度（尺寸）决定元素排列方式

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>媒体查询</title>
    <style>
        #div0 {
            width: 100%;
            height: 500px;
        }
        
        #div0 div {
            float: left;
            height: 100px;  
        }
        /* 1行三个div */
        @media screen and (min-device-width:400px){
            #div0 div {
                width: 33.3%;
            }
            #div0 div:nth-child(1) {
                background-color: red;
            }
            #div0 div:nth-child(2) {
                background-color: blue;
            }
            #div0 div:nth-child(3) {
                background-color: green;
            }
        }
        /* 2行三个div */
        @media screen and (min-device-width:300px) and (max-device-width:399px) {
            #div0 div {
                width: 50%;
            }
            #div0 div:nth-child(1) {
                background-color: red;
            }
            #div0 div:nth-child(2) {
                background-color: blue;
            }
            #div0 div:nth-child(3) {
                background-color: green;
            }
        }
        /* 3行三个div */
        @media screen and (min-device-width:200px) and (max-device-width:299px) {
            #div0 div {
                width: 100%;
            }
            #div0 div:nth-child(1) {
                background-color: red;
            }
            #div0 div:nth-child(2) {
                background-color: blue;
            }
            #div0 div:nth-child(3) {
                background-color: green;
            }
        }
    </style>
</head>
<body>
    <div id="div0">
        <div></div>
        <div></div>
        <div></div>
    </div>
</body>
</html>
```

