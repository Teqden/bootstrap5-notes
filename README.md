<h1>Bootstrap 学习笔记</h1>

这是我观看 B 站视频 [优极限-2021最新完整版bootstrap教程-乐字节全栈念小安](https://www.bilibili.com/video/BV1TU4y1p7zU?spm_id_from=333.788.videopod.episodes&vd_source=1d1e1ee322fb5e86e15f95cb909ee1be) 学习Bootstrap的笔记，在过程中，我还参阅了[Bootstrap官方文档](https://getbootstrap.com/docs/5.3/getting-started/introduction/)。

## 1. 准备
### 1.1 安装使用
将下载完毕的bootstrap源代码中的dist文件夹，整个复制到项目文件夹中，但一般需要重新命名此文件夹。

### 1.2 <meta>属性
- viewport：表示用户是否可以缩放页面
- width：视区的逻辑宽度，device-width：设定视区宽度为设备的屏幕宽度
- initial-scale：用于设置web页面的初始化缩放比例，设置其为1.0:显示未经缩放的web文档 

### 1.3 载入引入
1. 在title标签下，载入bootstrap的css：<br/>
```html
<link rel="stylesheet" href="bootstrap/css/bootstrap.min.css">
```
2. 在body标签中最下方，引入bootstrap的js组件：<br/>
```html
<script src="bootstrap/js/bootstrap.min.js"></script>
```

## 2. 布局容器
### 2.1 `.container` 固定宽度（两侧会有留白）
```html
<div class="container" style="background-color: yellowgreen;height: 100px;">Lorem ipsum dolor sit amet consectetur adipisicing elit.</div>
```

### 2.2 `.container-fluid` 100%宽度（占据全部视口）
```html
<div class="container-fluid" style="background-color: yellowgreen;height: 100px;">Lorem ipsum dolor sit amet consectetur adipisicing elit.</div>
```

## 3. 栅格网格系统
### 3.1 列元素
Bootstrap默认已将可见视口分为12列。如果在不同屏幕上需要不同的排列效果（如：中屏四八分，小屏六六分），可以在写元素时就加上对应的类名。
- col-xs-数值(超小屏：手机（<768px）)
- col-sm-数值(小屏：平板（>=768px）)
- col-md-数值(中屏：电脑（>=992px）)
- col-lg-数值(大屏（>=1200px）)

### 3.2 列组合
列的总数不能超过12，当超过12时，超出的部分会转行显示。

### 3.3 列偏移
当不希望相邻两个列紧靠在一起，但又不想使用margin来处理时，可以使用`offset-md-数值` 对列进行偏移，但一行中列的总数依然得<=12，否则将转行显示。<br/>
```html
<div class="row">
    <div class="col-md-1" style="background-color: aqua;">1</div>
    <div class="col-md-1 offset-md-1" style="background-color:bisque;">1</div>
    <div class="col-md-1 offset-md-2" style="background-color: aqua;">1</div>
    <div class="col-md-1 offset-md-3" style="background-color:bisque;">1</div>
</div>
```

### 3.4 列排序
改变列的方向使其左右浮动，并设置浮动距离，可通过 `col-md-push-数值（向左）` 和 `col-md-push-数值（向右）` 实现;当A移动到B列，而B列位置上本身有元素时，B列的元素会被A覆盖掉。

### 3.5 列嵌套
可以在一个列中继续添加一个或多个行容器，然后再在行容器中插入列元素。<br/>
```html
<div class="row">
            <div class="col-md-6" style="background-color: blue;">
                <div class="row">
                    <div class="col-md-1" style="background-color: chocolate;">1</div>
                    <div class="col-md-1" style="background-color:darkgreen;">1</div>
                    <div class="col-md-1" style="background-color: cornflowerblue;">1</div>
                    <div class="col-md-9" style="background-color:darkorchid;">9</div>
                </div>
            </div>
            <div class="col-md-6" style="background-color: brown;">6</div>
        </div>
```

## 4. 常用样式
### 4.1 标题
bootstrap对标题效果进行了修改并覆盖，并提供了.h1-.h6的对应类名，用以给非标题元素设置样式。
```html
<h1>标题1<small>副标题1</small></h1>
<h2>标题2<span class="small">副标题2</span></h2>
<div class="h1">你好</div>
```

### 4.2 段落
- `<small>` / `.small`：小字号
- `<b>` / `<strong>`：加粗
- `<i>` / `<em>`：斜体
- `.lead`：突出强调内容，增大加粗文本，并对其行高及margin作出相应处理 
- `<mark>` / `.mark`：高亮显示
- `<del>` / `<s>` / `.text-decoration-line-through`：删除线
- `<ins>` / `<u>` / `.text-decoration-underline`：下划线
<p class="lead">Lorem <small class=".text-decoration-line-through">ipsum</small> <mark>dolor</mark> sit <b class="text-decoration-underline">amet</b> consectetur <i>adipisicing</i> elit. <em>Nulla</em>, <strong>dolores</strong>?</p>

```html
    <p class="lead">Lorem <small class=".text-decoration-line-through">ipsum</small> <mark>dolor</mark> sit <b class="text-decoration-underline">amet</b> consectetur <i>adipisicing</i> elit. <em>Nulla</em>, <strong>dolores</strong>?</p>
```

### 4.3 强调
- `.text-muted`：提示，使用浅灰色（#999）
- `.text-primary`：主要，使用蓝色（#428bca）
- `.text-success`：成功，使用浅绿色（#3c763d）
- `.text-info`：通知信息，使用浅蓝色（#31708f）
- `.text-warning`：警告，使用黄色（#8a6d3b）
- `.text-danger`：危险，使用褐色（#a94442）
```html
<div class="text-primary">主要效果</div>
```

### 4.4 对齐
在css中常使用`text-align`实现文本的对齐，而bootstrap则通过四个类名控制文本的对齐风格：
- `.text-left`：左对齐
- `.text-center`：居中对齐
- `.text-end`：右对齐
- `.text-justify`：两端对齐（bootstrap5移除了text-justify类）
```html
    <div class="text-center">居中对齐</div>
```

## 补充：小技巧
1. 输入`!`然后敲击`enter`，可以自动生成基本的html结构
2. 直接输入`.test`然后敲击`enter`，可直接创建包含test类的div元素；#test 则是id为test的div元素
3. 直接输入`lorem`然后敲击`enter`，可生成填充性文档;输入`lorem3`可生成三个单词，输入`lorem*3`可生成三段话。
