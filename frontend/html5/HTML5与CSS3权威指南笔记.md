# HTML5与HTML4的区别

## 语法改变

* DOCTYPE声明

html5中DOCTYPE统一为 `<!DOCTYPE html>`

* 指定字符编码

html5推荐使用utf-8，即 `<meta charset="utf-8">`

## 元素新增与废除

* 新增的结构元素

    * `<header>`：内容区块或整个页面的标题
    * `<main>`：主要内容区块
    * `<footer>`：内容区块或整个页面的脚注
    * `<section>`：段落，章节
    * `<article>`：独立的文章
    * `<aside>`：独立的文章的辅助信息，与article连用
    * `<nav>`：导航链接

* 新增的非结构元素

    * `<video>`：视频
    * `<audio>`：音频
    * `<mark>`：标注
    * `<canvas>`：画布
    * `<menu>`：菜单
    * `<dialog>`：对话框

* 废除的元素

    * 废除的元素基本上都没有用过，不列出

## 属性新增与废除

* 新增的表单属性

    * `autofocus`：input，select，textarea与button元素指定，画面打开时自动获得焦点
    * `placeholder`：input，textarea指定，提示输入
    * `form`：input，output，select，textarea，button，fieldset指定，声明属于哪个表单，可以将其放在页面的任何位置，而非表单内部
    * `reauired`：input，textarea指定，检查该元素必须要有输入内容




