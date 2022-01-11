>- markdown用的地方确实很多，也很方便。自从学会这个，jupyter notebook都更好用了。
- 以下都是在atom Markdown Preview插件亲测有效的。


# 一、标题
在想要设置为标题的文字前面加#来表示
# 这是一级标题
## 这是二级标题
### 这是三级标题
#### 这是四级标题
##### 这是五级标题
###### 这是六级标题

# 二、字体
示例：
**这是加粗的文字**
*这是倾斜的文字*
***这是斜体加粗的文字***
~~这是加删除线的文字~~



<font face="黑体">我是黑体字</font>
<font face="微软雅黑">我是微软雅黑</font>
<font face="STCAIYUN">我是华文彩云</font>
<font color=#0099ff size=7 face="黑体">color=#0099ff size=72 face="黑体"</font>
<font color=#00ffff size=72>color=#00ffff</font>
<font color=gray size=72>color=gray</font>

<table><tr><td bgcolor=#FF1500>这里的背景色是：OrangeRed， 十六进制颜色值：#FF4500， rgb(255, 69, 0)</td></tr></table>

# 三、引用
在引用的文字前加>即可。引用也可以嵌套，如加两个>>三个>>>
n个...
貌似可以一直加下去，但没神马卵用
示例：
>这是引用的内容
>>这是引用的内容
>>>>>>>>>>这是引用的内容

# 四、分割线
三个或者三个以上的 - 或者 * 都可以。
示例：
---
----
***
*****

# 五、图片
语法：
![图片alt](图片地址 "图片title")

图片alt就是显示在图片下面的文字，相当于对图片内容的解释。
图片title是图片的标题，当鼠标移到图片上时显示的内容。title可加可不加

示例：
![blockchain](https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/
u=702257389,1274025419&fm=27&gp=0.jpg "区块链")

# 六、超链接
1. markdown语法：
[超链接名](超链接地址 "超链接title")
title可加可不加

#### 示例1：
[简书](http://jianshu.com)
[百度](http://baidu.com)

注：Markdown本身语法不支持链接在新页面中打开，貌似简书做了处理，是可以的。别的平台可能就不行了.

2. 如果想要在新页面中打开的话可以用html语言的a标签代替。
<a href="超链接地址" target="_blank">超链接名</a>

#### 示例2
<a href="https://www.jianshu.com/u/1f5ac0cf6a8b" target="_blank">简书</a>

3. 参考式的链接
  - 在链接文字的括号后面再接上另一个方括号，而在第二个方括号里面要填入用以辨识链接的标记。
  - 在两个方括号中间加上一个空格。接着，在文件的任意处，你可以把这个标记的链接内容定义出来。

#### 示例3
I get 10 times more traffic from [Google] [1] than from [Yahoo] [2] or [MSN] [3].

  [1]: http://google.com/        "Google"
  [2]: http://search.yahoo.com/  "Yahoo Search"
  [3]: http://search.msn.com/    "MSN Search"
#### 示例4
I get 10 times more traffic from [Google][] than from
[Yahoo][] or [MSN][].

  [google]: http://google.com/        "Google"
  [yahoo]:  http://search.yahoo.com/  "Yahoo Search"
  [msn]:    http://search.msn.com/    "MSN Search"

# 七、列表
#### 1.无序列表
语法：
无序列表用 - + * 任何一种都可以
- 列表内容
+ 列表内容
* 列表内容

注意：- + * 跟内容之间都要有一个空格

#### 2. 有序列表
语法：
数字加点
1. 列表内容
2. 列表内容
3. 列表内容

注意：序号跟内容之间要有空格

#### 3. 列表嵌套
上一级和下一级之间敲三个空格或者一个tab即可

- 一级无序列表内容
  - 二级无序列表内容
  + 二级无序列表内容
  * 二级无序列表内容


1. 一级有序列表内容
  1. 二级有序列表内容
  2. 二级有序列表内容
  3. 二级有序列表内容

1. 一级有序列表内容
  - 二级无序列表内容
  - 二级无序列表内容
  + 二级无序列表内容


# 八、表格
语法：

一个普通标题|一个普通标题 | 一个普通标题
------ | ------ | ------
短文本 | 中等文本 | 稍微长一点的文本
稍微长一点的文本 | 短文本 | 中等文本

第二行分割表头和内容。
- 有一个就行，为了对齐，多加了几个
文字默认居左
- 两边加：表示文字居中
- 右边加：表示文字居右

注：原生的语法两边都要用 | 包起来。此处省略

示例：

| 姓与名 | 技能 | 排行榜 |
| :---- | :---: | ---: |
| 刘备 | 哭 | 大哥 |
| 关羽|打|二哥|
|张飞|骂|三弟|



# 九、代码
语法：
单行代码：代码之间分别用一个反引号包起来
    `代码内容`

代码块：代码之间分别用三个反引号包起来，且两边的反引号单独占一行
(```)
  代码...
  代码...
  代码...
(```)

注：为了防止转译，前后三个反引号处加了小括号，实际是没有的。这里只是用来演示，实际中去掉两边小括号即可。

##### 示例：
单行代码
`create database hero;`

代码块
```
    function fun(){
         echo "这是一句非常牛逼的代码";
    }
    fun();
```


# 十、流程图

```mermaid
graph TD
  st=>start: 开始
  op=>operation: My Operation
  cond=>condition: Yes or No?
  e=>end
  st->op->cond
  cond(yes)->e
  cond(no)->op
```
```flow
st[注册印象笔记]-->a
a{是否已经购买马克飞象}
a-->|是|b1(您已购买马克飞象可以使用markdown语法)
a-->|否|b2(您还未能成功购买马克飞象但你可以免费试用10天)
b1-->c[欢迎使用马克飞象]
b2-->d{是否要购买马克飞象}
d-->|是|e1(您已成功购买马克飞象欢迎使用)
e1-->c
d-->|否|e2(试用10天后将会到期欢迎购买)
```
