```json
{
  "date": "2024.07.03 18:05",
  "tags": ["web"],
  "description":"在蓝桥杯备赛期间整理了一份web开发笔记，包括css布局，js，jquery等等实用技术知识"
}
```
# web笔记

## css

### :nth-of-type()	:nth-child()

- `:nth-of-type()`只算制定类型的标签；`:nth-child()`把所有子标签计算在内，一般用在父选择器上
- 下标`1`开始



### flex布局

- `flex-warp`： 元素放不下时换行/列



### transition

- 动画切换效果

```css
/* 第一个参数是属性名称，all指代全部 */
transition: all 0.3s ease-in-out;
```



### transform

- 控制元素变形

    1. **`rotate()`:**
       - `rotate()` 函数用于旋转元素。
       - 你需要指定一个角度，定义元素应该旋转多少度。正值表示顺时针旋转，负值表示逆时针旋转。
       - 例如：`transform: rotate(45deg);` 会将元素顺时针旋转 45 度。
    
    2. **`scale()`:**
       - `scale()` 函数用于改变元素的大小。
       - 你可以指定一个缩放因子，定义元素应该被放大或缩小多少。大于 1 的值会放大元素，0 到 1 之间的值会缩小元素，负值会反转元素。
       - 例如：`transform: scale(2);` 会将元素的大小放大到原来的两倍。
    
    3. **`translate()`:**
       - `translate()` 函数用于移动元素。
       - 你需要指定元素应该移动的 X 轴和 Y 轴的距离。可以使用长度单位，如像素或百分比。
       - 例如：`transform: translate(50px, 100px);` 会将元素向右移动 50 像素，向下移动 100 像素。
    
    4. **`skew()`:**
       - `skew()` 函数用于倾斜元素。
       - 你需要指定元素在 X 轴和 Y 轴的倾斜角度。正值表示顺时针倾斜，负值表示逆时针倾斜。
       - 例如：`transform: skew(30deg, 20deg);` 会在 X 轴方向将元素顺时针倾斜 30 度，在 Y 轴方向顺时针倾斜 20 度。
  
    这些函数可以单独使用，也可以组合使用，实现更复杂的变换效果。例如：`transform: rotate(30deg) scale(1.5) translate(100px, 50px) skew(10deg, 20deg);` 会将元素旋转、缩放、移动和倾斜。

### 属性选择器

```css
//所有有herf属性的元素
[href] {
    color: blue;
}

//该属性的指定标签
input[type="text"] {
    border-color: green;
}

//包含独立单词button，不是正则匹配
[class~="button"] {
    background-color: yellow;
}

//en或以en-开头
[lang|="en"] {
    font-size: 14px;
}

//https开头
[src^="https"] {
    border: 1px solid black;
}

//.pdf结尾
[href$=".pdf"] {
    color: red;
}

//类似正则匹配
[class*="text"] {
    font-style: italic;
}
```



### 首字母大写

```css
.capitalize {
  text-transform: capitalize;
}
```





## js

### localStorage

`localStorage` 是 Web Storage API 的一部分，它允许你在用户的浏览器中存储键值对数据。与 cookies 不同，存储在 `localStorage` 中的数据没有到期时间，数据会保留到明确通过 JavaScript 或用户清除浏览器缓存被删除。



### window对象
#### 属性
- **window.document**: 指向加载在窗口中的文档对象（DOM）。
- **window.location**: 包含有关当前 URL 的信息。
- **window.localStorage**: 提供对本地存储的访问，允许你存储键值对。
- **window.sessionStorage**: 提供对会话存储的访问，类似于 localStorage 但是更短暂。
- **window.innerWidth/innerHeight**: 浏览器窗口的内部宽度/高度。
- **window.outerWidth/outerHeight**: 浏览器窗口的外部宽度/高度。
- **window.screenX/screenY**: 窗口相对于屏幕左上角的 X 和 Y 坐标。
- **window.screen**: 包含有关用户屏幕的信息。
- **window.history**: 提供对浏览器历史的操作能力。

#### 方法

- **window.alert()**: 显示一个带有消息和一个确认按钮的警告框。
- **window.confirm()**: 显示一个带有消息和确认及取消按钮的对话框。
- **window.prompt()**: 显示一个带有消息和输入框及确认取消按钮的对话框。
- **window.open()**: 打开一个新的浏览器窗口或标签页。
- **window.close()**: 关闭当前窗口。
- **window.setTimeout()**: 在指定的毫秒数后执行函数。
- **window.clearTimeout()**: 取消由 `setTimeout()` 设置的超时。
- **window.setInterval()**: 按照指定的周期（以毫秒计）来调用函数或计算表达式。
- **window.clearInterval()**: 取消由 `setInterval()` 设置的定时执行操作。
- **window.scrollTo(x, y)**: 滚动到文档中的特定位置。



### .style.classList

- add() 

```js
// 添加两个类
element.classList.add('class1', 'class2');
```

- remove()

```js
// 移除两个类
element.classList.remove('foo', 'bar');
```

- contains()

```js
//检查是否包含active类
item.classList.contains('active')
```



### Array

#### .every()

- 遍历数组，返回一个布尔值，用来检测数组中元素是否都符合参数中函数的要求。



#### .includes()

- 检查数组中是否有指定元素



### RegExp

#### 模版字符串生成正则表达式

- 第二个参数表示搜索标志，多个标志写在一起

```js
let reg = RegExp(`^.*${this.inputValue}.*$`, 'i');

let reg = RegExp(`^.*${this.inputValue}.*$`, 'ig');
```



### json类





## axios



## vue

### @input

- input框可以绑定事件`input`，每次输入框中内容发生变化时就会触发事件



## jquery

### $("selector")

- 用于得到jQuery对象
- `selector`可以是任何css选择器



### $(window)

1. **事件绑定**：可以绑定各种事件监听器到窗口对象上，例如 `resize`、`scroll`、`load` 等。
   
   - **resize**：当窗口大小变化时触发。
     ```javascript
     $(window).resize(function() {
       console.log("Window size changed!");
     });
     ```
   
   - **scroll**：当用户滚动窗口时触发。
     ```javascript
     $(window).scroll(function() {
       console.log("Window scrolled!");
     });
     ```
   
   - **load**：当页面加载完成时触发。
     ```javascript
     $(window).on('load', function() {
       console.log("Window loaded!");
     });
     ```

2. **尺寸获取**：可以获取窗口的尺寸（宽度和高度）。
   - 获取窗口宽度和高度：
     ```javascript
     var width = $(window).width();
     var height = $(window).height();
     ```

3. **滚动控制**：可以控制窗口的滚动位置。
   - 滚动到页面顶部：
     ```javascript
     $(window).scrollTop(0);
     ```

4. **视口信息**：可以获取有关视口的信息，如滚动位置。
   - 获取滚动位置：
     ```javascript
     var scrollTop = $(window).scrollTop();
     ```



### .eq()

- 从jQuery对象集合中选取一个特定索引位置的元素。

- 用法

```javascript
$("#lift>a").eq(i).addClass("active-color")
```



### .find()

- 查找这个jQuery对象中的所有指定对象
- 参数可以是任意css选择器

```javascript
$(".container div[class*=lump]").eq(pos).find("img").length
```



### .val()

- 对于`input`，`option`等标签可以用`val()`获取其`value`。

```javascript
lumps.eq(pos + ($('.process input').val() * 1)).addClass("active")
```



### .text()	.html()

- 对应原生js的`innerText`和`innerHTML`。



### .addClass()	.removeClass()

- 增加和删除指定类名

```js
// 添加两个类
$('#myElement').addClass('class1 class2');

// 移除两个类
$('#myElement').removeClass('foo bar');

```



### .each()

- 遍历jQuery对象数组，第一个参数`index`，第二个`item`
- `return false`中断遍历

```js
liList.each((index, item) => {
    if (item.classList.contains('active') && index<2) {
      item.classList.remove('active');
      liList[index + 1].classList.add('active');
      return false;
    }
  });
```



### .parent()

- 用来选取指定元素的父亲元素
- 可以用在点击事件

```js
//this是触发点击事件的元素
$(this).parent()
```



### .prev()	.next()

- 用来选取同级的上一个/下一个元素

```js
$(this).parent().next();
$(this).parent().prev();
```



### 相关函数列举

1. **类操作相关函数**:
   - `.addClass(className)`: 向选定的元素添加一个或多个类名。
   - `.removeClass(className)`: 从选定的元素中移除一个或多个类名。
   - `.toggleClass(className)`: 对选定的元素进行类名的切换。如果类名存在，则移除它；如果类名不存在，则添加它。
2. **样式操作相关函数**:
   - `.css(propertyName, value)`: 设置选定元素的 CSS 属性。
   - `.css(propertyName)`: 获取选定元素的 CSS 属性值。
   - `.hide()`: 隐藏选定的元素。
   - `.show()`: 显示选定的元素。
   - `.toggle()`: 切换选定元素的可见状态。
3. **属性操作相关函数**:
   - `.attr(attributeName, value)`: 设置选定元素的属性值。
   - `.attr(attributeName)`: 获取选定元素的属性值。
   - `.removeAttr(attributeName)`: 移除选定元素的属性。
4. **事件处理相关函数**:
   - `.click()`: 绑定点击事件处理器到选定的元素或触发选定元素的点击事件。
   - `.bind(eventType, eventHandler)`: 绑定一个事件处理器到选定的元素。
   - `.unbind(eventType, eventHandler)`: 移除选定元素的事件处理器。
   - `.on(eventType, selector, data, function)`: 在选定元素上绑定一个或多个事件的事件处理函数。
   - `.off(eventType, selector, function)`: 移除由 `.on()` 方法添加的事件处理器。
5. **动画和效果相关函数**:
   - `.fadeIn(duration)`: 逐渐改变选定元素的不透明度，直到完全显示。
   - `.fadeOut(duration)`: 逐渐改变选定元素的不透明度，直到完全隐藏。
   - `.slideUp(duration)`: 用滑动效果隐藏选定的元素。
   - `.slideDown(duration)`: 用滑动效果显示选定的元素。
   - `.animate(properties, duration, easing, complete)`: 对选定元素进行自定义动画效果。



### eventType列举

1. **鼠标事件**:
   - `click`: 当用户点击元素时触发。
   - `dblclick`: 当用户双击元素时触发。
   - `mouseenter`: 当鼠标指针进入元素时触发。
   - `mouseleave`: 当鼠标指针离开元素时触发。
   - `mousemove`: 当鼠标指针在元素内部移动时触发。
   - `mouseover`: 当鼠标指针位于元素上方时触发。
   - `mouseout`: 当鼠标指针离开元素时触发。
   - `mousedown`: 当鼠标按钮被按下时触发。
   - `mouseup`: 当鼠标按钮被释放时触发。

2. **键盘事件**:
   - `keydown`: 当用户按下键盘键时触发。
   - `keyup`: 当用户释放键盘键时触发。
   - `keypress`: 当用户按下键盘键时触发（已废弃，不推荐使用）。

3. **表单事件**:
   - `submit`: 当表单被提交时触发。
   - `change`: 当表单元素的值改变时触发。
   - `focus`: 当元素获得焦点时触发。
   - `blur`: 当元素失去焦点时触发。
   - `select`: 当用户选择文本框中的一或多个字符时触发。

4. **文档/窗口事件**:
   - `load`: 当元素（如文档和图片）已加载时触发。
   - `unload`: 当文档被完全卸载时触发。
   - `resize`: 当窗口或框架被调整大小时触发。
   - `scroll`: 当用户滚动指定的元素时触发。

5. **触摸事件**:
   - `touchstart`: 当触摸点被放置在触摸屏上时触发。
   - `touchmove`: 当触摸点在屏幕上移动时触发。
   - `touchend`: 当触摸点离开屏幕时触发。

6. **其他事件**:
   - `contextmenu`: 当尝试打开上下文菜单时触发（通常是通过右键点击）。
   - `error`: 当发生错误时触发。



## echart

### 关键函数

1. **echarts.init(dom, theme, opts)**: 初始化一个 ECharts 实例。`dom` 是要绑定的 DOM 元素，`theme` 是可选的主题名称，`opts` 是初始化时的额外选项。
2. **setOption(option, notMerge, lazyUpdate)**: 设置 ECharts 实例的配置项。`option` 是包含配置信息的对象，`notMerge` 控制是否合并配置项或全新替换，`lazyUpdate` 控制是否延迟更新。
3. **resize([opts])**: 调整图表大小，确保在容器大小变化时图表也相应更新。
4. **dispose()**: 销毁图表实例，释放内存。

### 关键词和属性

1. **title**: 图表标题，包含 `text`、`subtext` 等属性。
2. **xAxis/yAxis**: 坐标轴配置，包括类型（`type`），数据（`data`），坐标轴标签（`axisLabel`）等。
   - `type`: 常用类型包括 `"category"`（类目轴）、`"value"`（数值轴）、`"time"`（时间轴）等。
   - `data`: 在 `type` 为 `"category"` 时，定义类目数据。
3. **series**: 系列列表。每个系列通过 `type` 定义图表类型（如 `"line"`、`"bar"`、`"pie"` 等），并包含相应类型的特定配置和数据。
4. **legend**: 图例配置，控制图例的显示、位置等。
5. **tooltip**: 提示框配置，控制鼠标悬停时显示的信息内容和样式。
6. **grid**: 网格配置，主要用于直角坐标系内绘图网格的定义。
7. **toolbox**: 工具箱配置，提供导出、数据视图、动态类型切换等工具功能。

```js
var option = {
    tooltip: {
        trigger: 'axis', // 触发类型：坐标轴触发
        axisPointer: {  // 坐标轴指示器配置项
            type: 'cross', // 十字准星指示器
            label: {
                backgroundColor: '#6a7985'
            }
        }
    },
    legend: {
        data: ['系列1', '系列2'] // 图例的数据数组
    },
    toolbox: {
        feature: {
            saveAsImage: {}, // 保存为图片工具
            dataView: {}, // 数据视图工具
            restore: {}, // 配置项还原
            dataZoom: {}, // 区域缩放
            magicType: { // 动态类型切换
                type: ['line', 'bar'] // 切换为折线图，柱状图
            }
        }
    },
    grid: {
        left: '3%', // grid 组件离容器左侧的距离
        right: '4%',
        bottom: '3%',
        containLabel: true // grid 区域是否包含坐标轴的刻度标签
    },
    xAxis: {
        type: 'category',
        boundaryGap: false,
        data: ['标签1', '标签2', '标签3', '标签4', '标签5', '标签6', '标签7']
    },
    yAxis: {
        type: 'value'
    },
    series: [
        {
            name: '系列1',
            type: 'line',
            stack: '总量',
            data: [120, 132, 101, 134, 90, 230, 210]
        },
        {
            name: '系列2',
            type: 'line',
            stack: '总量',
            data: [220, 182, 191, 234, 290, 330, 310]
        }
    ]
};

```



## node

```bash
node ./index.js
```





## 其他















pinia用法

animation，transition

mounted， onMounted

emit

vue-router的history

pinia的defineStore写法





flex布局 grid布局

background

css各种选择器

before？ hover？
