
# 常用快捷键
| **Command**                  |    **Key**    |
| :--------------------------- | :-----------: |
| 粗体                         |    Ctrl+B     |
| 斜体                         |    Ctrl+I     |
| 删除线                       |     Alt+S     |
| 标题(uplevel)                | Ctrl+Shift+]  |
| 标题(downlevel)              | Ctrl+Shift+[  |
| 包裹数学公式                 |    Ctrl+M     |
| Check/Uncheck task list item |     Alt+C     |
| list中的代码块               | Enter Tab Tab |
| 格式化table                  |  Alt+Shift+F  |
![格式化table](https://raw.githubusercontent.com/yzhang-gh/vscode-markdown/master/images/gifs/table-formatter.gif)

# markdown常用命令
| 作用           |                   命令                   |
| :------------- | :--------------------------------------: |
| 强调           |           `*强调*`或者`_强调_`           |
| 链接           |  `[这是个链接](https://this.is.a/url)`   |
| 引用里面插链接 | >内容[链接](https://xxx.xxx.xxx)内容n... |

# 一些有用的命令
- Markdown: Create Table of Contents: 创建目录: F1/Ctrl+Shift+P --> ctoc
- Markdown: Update Table of Contents: 更新目录: F1/Ctrl+Shift+P --> utoc
- Markdown: Toggle code span: 选中的作为代码块: F1/Ctrl+Shift+P --> tcs
- Markdown: Print current document to HTML: 把当前文件输出为html


![本地图片](./resources/127345.png "需上传github后引用,否则作blog图片会失效")

*如果你的markdown在一个文件目录下，需要添加另一个目录下的图片，绝对路径是不可行的。需要 “迂回”
所谓 迂回，即需要先用../../命令返回上一文件目录，直至可以顺利找到要添加图片的目录。*

[markdown常用语法手册](https://blog.rxliuli.com/p/5042aac0/)
<br/>

# 特殊字符
| 特殊字符 | 转义方法 |
| :------- | :------: |
| <        |  `&lt;`  |
| &        | `&amp;`  |
| \#       |   `\#`   |
| \\       |   `\\`   |
.**或者用两个 ` 来框住特殊字符**<br/>
.**一般都是用\转义**

# 小技巧
## 如何在列表中插入表格table
```table区块整个缩进一下就好了。```