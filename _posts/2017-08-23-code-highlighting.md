---
layout: post
title: "简单记录 Markdown 语法和代码高亮功能"
description:
categories: [Markdown]
tags: [jekyll, Markdown]
redirect_from:
  - /2017/08/23/
---

> 这是 [Simple Texture][Simple Texture] 主题的 [kramdown][kramdown] 格式以及代码模块和高亮功能测试页面

目录索引功能（Kramdown table)
* Kramdown table of contents
{:toc .toc}

# 一级标题

## 二级标题

### 三级标题

#### 四级标题

##### 五级标题

###### 六级标题

这是一个段落。

这是一个跳转到我的主页的[链接](https://caiyangmin.github.io)。
一个[链接](https://caiyangmin.github.io/blog "我的博客")同样可以有标题。

这是 **粗体字。**

这是 *斜体字。*

这是 ***加粗斜体字体。***

这是一个注脚[^1]。

这是极少人知道的模仿键盘文本 <kbd>keyboard text</kbd> 标签，还有通常的代码风格标签 `<code>`

这个表示插入文本（下划线） <ins>inserted</ins>

这个同样表示强调斜体文本 _italicize_

这个 tag 会在文本上加上删除线 <strike>strikeout text</strike>

## Blockquotes 引用

> 引用里的段落
>
> 以上

### Nested 嵌套

> 这是引用里的一个段落
> 。
> > 一个嵌套引用
> 结束

### Lists inside 引用内的列表

> Unordered Lists 无序列表
> * lists one
> * lists two
> * lists three
>
> Ordered lists 有序列表
> 1. lists one
> 2. lists two
> 3. lists three

### long lines 长句引用
> Github Pages可以看成是GitHub免费托管的wiki site，主要是为GitHub repository服务的，让原来乱七八糟的wiki有一个统一的格式，用的MarkDown [Markdown Basics](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)（越来越多的网站，client都转到用 MD语法了，国内的简书，国外的medium）。之所以选择MarkDown，也是为了我们广大程序员，喜好VIM的编辑风格（像黑客一样写作），这样可以通过写简单的plain text，就能在HTML上面解释成漂亮的网页。

## Lists 列表

* list 1 item 1
  * nested list item 1
  * nested list item 2
  * nested list item 3 with blockquote
> ruby -v
>
> tsc -v
* list 1 item 2
* list 1 item 3

## Tables 表格

* Table 1

  |-----------------+---------------+---------------+---------------|
  | Default aligned | Left aligned | Center aligned | Right aligned |
  |-----------------|:-------------|:---------------|:--------------|
  | First body part	| Second cell	 | Third cell	    | fourth cell   |
  | Second line	    | foo	         | **strong**     |	baz           |
  | Third line	    | quux         | baz            |	bar           |
  | Footer row	 	 	|              |                |               |
  |-----------------+--------------+----------------+---------------|

* Table 2

  |---
  | Default aligned	| Left aligned | Center aligned	| Right aligned |
  |-|:-|:-|-:
  | First body part |	Second cell |	Third cell |	fourth cell
  | Second line |	foo |	strong |	baz
  | Third line |	quux |	baz |	bar
  | Footer row

## Horizontal Rules 横线/分割线规则

* * *

---

  _  _  _  _

----------------

## Images

![smiley](https://kramdown.gettalong.org/overview.png)


# Code Spans

这是一个内嵌 codeblocks 的测试，像 `C:/Ruby23-x64` 或者 `SELECT "offices".*FROM "offices" `

Here is a literal `` ` `` backtick
还有一些 Ruby 的代码片段 `x = Class.new`{:.language-ruby}

# Fenced Code Blocks

代码和符号
~~~~~~~~~~~~~~~~
~~~~~~~~~~
code with tildes
~~~~~~~~~~
~~~~~~~~~~~~~~~~

# Simple codeblock with long lines

    function myFunction() {
        alert("Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.");
    }

# Language of Code Blocks

~~~ ruby
def what?
  42
end
~~~

# Highlighted

## External Gist

<script
src="https://gist.github.com/yizeng/9b871ad619e6dcdcc0545cac3101f361.js"></script>

## Simple Highlight with Ruby

{% highlight ruby %}
def foo
  puts 'foo'
end
{% endhighlight %}

## Highlight with long lines with C#
{% highlight c# %}
public class Hello {
  public static void Main() {
    Console.WriteLine("Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.");
  }
}
{% endhighlight %}

## Highlight with line numbers and long lines with javascript

{% highlight javascript linenos=table %}
function myFunction() {
  alert("Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.");
}
{% endhighlight %}

[^1]: This is a footnote

[kramdown]: https://kramdown.gettalong.org/
[Simple Texture]: https://github.com/yizeng/jekyll-theme-simple-texture
