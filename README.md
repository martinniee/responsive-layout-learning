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

### 引入方式1

对案例2的改进

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>媒体查询</title>
    <!-- 提取公共样式 -->
    <style>
        #div0 {
            width: 100%;
            height: 500px;
        }
        #div0 div {
            float: left;
            height: 100px;
        }
    </style>
    <!-- 设置媒体查询样式 -->
    <!-- 3行三个div -->
    <style media="(min-device-width:200px) and (max-device-width:299px)">
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
    </style>
    <!-- 2行三个div -->
    <style media="(min-device-width:300px) and (max-device-width:399px)">
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
    </style>
    <!-- 1行三个div -->
    <style media="(min-device-width:400px)">
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

### 引入方式2

对案例2的改进-采用外部css样式

**1，HTML部分**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>媒体查询</title>
    <!-- 引入公共样式 common.css -->
    <link rel="stylesheet" href="./css/common.css" >
    <!-- 引入媒体查询 样式 css1.css -->
    <link rel="stylesheet" href="./css/css1.css" media="(min-device-width:200px) and (max-device-width:299px)">
    <!-- 引入媒体查询 样式 css2.css -->
    <link rel="stylesheet" href="./css/css2.css" media="(min-device-width:300px) and (max-device-width:399px)">
    <!-- 引入媒体查询 样式 css3.css -->
    <link rel="stylesheet" href="./css/css3.css" media="(min-device-width:400px)">
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

**2，CSS部分**

文件结构说明

```bash
.
├── css/
│   ├── common.css
│   ├── css1.css
│   ├── css2.css
│   └── css3.css
└── 04_media_query.html
```

```css
/* common.css */
/* 公共样式css */
#div0 {
    width: 100%;
    height: 500px;
}
#div0 div {
    float: left;
    height: 100px;
}
/* 子元素背景 */
#div0 div:nth-child(1) {
    background-color: red;
}
#div0 div:nth-child(2) {
    background-color: blue;
}
#div0 div:nth-child(3) {
    background-color: green;
}
```

```css
/* css1.css */
/* 3行三个div */
#div0 div {
    width: 100%;
}
```


```css
/* css2.css */
/* 2行三个div */
#div0 div {
    width: 50%;
}
```


```css
/* css3.css */
/* 1行三个div */
#div0 div {
    width: 33.3%;
}
```

## flex弹性布局

FlexiableBox即是**弹性盒子**，用来进行弹性布局，可以配合rem处理尺寸的适配问题。

用来为盒状模型提供最大的灵活性。任何一个容器都可以指定为Flex布局。更加符合响应式设计的特点

**1，主轴和交叉轴**

平面分为水平和垂直两个方向，分别可称为`x`,`y`轴。元素的排列方式有两种，**水平排列**或**垂直排列**。

元素的排列方式决定布局的 **主轴 （main axis）**，与主轴相对的方向被称为 **交叉轴 （cross axis）**

flex布局结构示意图：

![image-20230531164115955](assets/README-images/image-20230531164115955.png)



### 主轴方向与换行

**1，主轴方向**

`flex-direction` 属性: 决定**元素在父元素盒子中的排列方式**

- row ：默认值, 元素 **从左到右**顺序显示
- row-reverse： 与 row 相反 元素从右到左顺序显示
- column ：元素 **从上到下**顺序显示
- column-reverse： 与 column 相反， 元素从下到上顺序显示

HTML

```html
<div id="div0">
        <div>1</div>
        <div>2</div>
        <div>3</div>
        <div>4</div>
</div>
```

CSS

```css
/* 设置父元素样式 */
#div0{
    width: 500px;
    background-color: violet;
    /* 给父元素 设置 display: flex 则子元素的布局会按照 flex布局排列 */
    display: flex;
    flex-direction: row-reverse;
}
/* 设置子元素样式 */
#div0 div{
    width: 100px;
    height: 100px;
    background-color: skyblue;
    border: 2px solid gold;
}
```

flex-direction布局示意图：

![flex-direction布局示意图](assets/README-images/image-20230531170423584.png)

注意事项：

- 设置flex布局后的子元素的水平宽度是根据**父元素宽度以及元素个数计算出来的数值**。
- 如果**计算的宽度小于元素自身设置的宽度**，则以计算的宽度为为准压缩元素，否则已元素自身宽度为最终宽度。



**2，换行**

flex-wrap 属性：决定子元素在父元素盒子中的是否换行（列）
- nowrap ： 默认值。不换行或不换列。
- wrap： 换行或换列。
- wrap-reverse：换行或换列，但以相反的顺序。

flex-direction 与 flex-wrap 合并的简写方式

flex-flow 属性

```css
/* 格式： */
flex-flow: <flex-direction>  <flex-wrap>
/* 例子： */
flex-flow: row wrap;
```

