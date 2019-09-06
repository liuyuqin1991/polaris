# 散装CSS

## position:fixed 降级问题

* 不知道曾经的你是不是遇到吸顶效果，就是使用 position:fixed 这个属性。其实如果其父元素中有使用 transform，fixed 的效果会降级为 absolute。
解决方案：
既然会降级为 absolute 效果，我们该怎么解决这个问题呢？我们就改考虑什么情况下 fixed 和 absolute 的表现效果会是一样的。
即当使用 fixed 的直接父元素的高度和屏幕的高度相同时 fixed 和 absolute 的表现效果会是一样的。

> 如果这个直接父级内的元素存在滚动的情况，那就加上 overflow-y: auto。

## 文字两端对齐

* 确定宽度后，再运用text-align和text-align-last
```
width:100px;
text-align: justify;
text-align-last:justify;
```

## 每个单词的首字母大写

* JS也能控制，但是CSS更加简单，只需要一句话

JS方法：
```
function capitalizeFirst( str ) {
    let result = '';
    result = str.toLowerCase().replace(/( |^)[a-z]/g, (L) => L.toUpperCase());
    return result
}  
```

CSS方法：
```
.capitalizeFirst-css {
    text-transform: capitalize;
}
```

text-transform 简单介绍

> 这是 CSS2 中的属性，参数有 capitalize | uppercase | lowercase | none

参数介绍：

none： 默认。定义带有小写字母和大写字母的标准的文本。
capitalize： 文本中的每个单词以大写字母开头。
uppercase： 定义仅有大写字母。
lowercase： 定义无大写字母，仅有小写字母。
