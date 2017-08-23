---
layout: post
title: "简单记录 Markdown 语法和代码高亮功能"
description:
categories: [tutorials]
tags: [jekyll]
redirect_from:
  - /2017/08/23/
---

> 这是 [Simple Texture][Simple Texture] 主题的代码模块和高亮功能测试页面

目录索引功能
* Kramdown table of contents
{:toc .toc}

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
