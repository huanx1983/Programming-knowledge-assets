1.是什么

+ HTML(HyperText Markup Language)是用来描述网页的一种标记语言,不是编程语言.
+ HTML是一套标记标签的集合,HTML文档包含了HTML标签及文本内容.
+ HTML使用标记标签来描述网页,HTML文档也叫做web页面,HTML运行于能解析HTML标签的解析器(浏览器)
+ HTML 是一种在Web上使用的通用标记语言。HTML允许你格式化文本，添加图片，创建链接、输入表单、框架和表格等等，并可将之存为文本文件，浏览器即可读取和显	示。
+ HTML 的关键是标签，其作用是指示将出现的内容。
	
2.形式
+ <标签>内容</标签>
+ <标签/>

        <!DOCTYPE html>     //html5        
        <html>
            <head>
                <title>页面标题</title>
                <meta charset="UTF-8">  <!--处理文字编码的乱码问题-->
            </head>
            <body>
                <h1>这是一个标题</h1>
                <p>这是一个段落。</p>
                <p>这是另外一个段落。</p>
            </body>
        </html>
Note:只有body区域才会在浏览器中显示。
	
3.版本
+ HTML          1991
+ HTML+         1993
+ HTML 2.0      1995
+ HTML 3.2      1997
+ HTML 4.01     1999
+ XHTML 1.0     2000
+ HTML5         2012
+ XHTML5        2013
	
	
4.HTML元素语法:

+ 元素(标签)
	HTML 元素以开始标签起始
	HTML 元素以结束标签终止
	元素的内容是开始标签与结束标签之间的内容
	某些 HTML 元素具有空内容（empty content）  ex:<br/>
	空元素在开始标签中进行关闭（以开始标签的结束而结束）
	大多数 HTML 元素可拥有属性
	
+ 属性
	HTML 元素可以设置属性
	属性可以在元素中添加附加信息
	属性一般描述于开始标签
	属性总是以名称/值对的形式出现，比如：name="value"
	
+ 适用于所有元素的属性
	class	为html元素定义一个或多个类名（classname）(类名从样式文件引入)
	id	定义元素的唯一id
	style	规定元素的行内样式（inline style）
	title	描述了元素的额外信息 (作为工具条使用)
	
	
4.标签

+ 根标签
	
	    <html>...</html>
	
	
+ body部分被浏览器UI化
	
	    <body>...</body>


+ 文档主体部分的标题
	
	    <h1>这是一个标题</h1>
	    <h2>这是一个标题</h2>
	    <h3>这是一个标题</h3>
	    <h6>这是一个标题</h6>
	
	
+ 段落,会自动站一新行
	
	    <p>这是一个段落。</p>
	    <p>这是另外一个段落。</p>
	
	
+ 换行(非新段落p)
	
	    <br/>
	
	
+ 水平线
	
	    <hr></hr>
	
	
+ link
	
	    <a href="http://www.baidu.com">这是一个链接</a>
	
	
+ 图片
	
	    <img src="abc.png" width="100" height="100">
	
	
+ <!-- 这是一个注释 -->
	
	
+ <strong> 替换加粗标签 <b>  
	  
	  
+ <em> 替换 <i>标签使用
	
+ 标签	

        HTML            文本格式化标签
        标签				描述
        <b>				定义粗体文本
        <em>			定义着重文字
        <i>				定义斜体字
        <small>			定义小号字
        <strong>		定义加重语气
        <sub>			定义下标字
        <sup>			定义上标字
        <ins>			定义插入字
        <del>			定义删除字
        
        
        HTML "计算机输出" 标签
        标签				描述
        <code>			定义计算机代码
        <kbd>			定义键盘码
        <samp>			定义计算机代码样本
        <var>			定义变量
        <pre>			定义预格式文本
        
        
        HTML 引文, 引用, 及标签定义
        标签				描述
        <abbr>			定义缩写
        <address>		定义地址
        <bdo>			定义文字方向
        <blockquote>	定义长的引用
        <q>				定义短的引用语
        <cite>			定义引用、引证
        <dfn>			定义一个定义项目
        
        
        
        
        HTML <head> 元素
	    <head> 元素包含了所有的头部标签元素。在 <head>元素中你可以插入脚本（scripts）, 样式文件（CSS），及各种meta信息。
	    可以添加在头部区域的元素标签为: <title>, <style>, <meta>, <link>, <script>, <noscript>, and <base>.
	
	    http://www.w3school.com.cn/html/html_quick.asp
	    http://www.w3school.com.cn/html/html5_intro.asp
	    http://www.w3school.com.cn/html/html5_browsers.asp


+ CSS

	形式:
	
	1.<head>
			<style type="text/css">
				body {background-color:yellow;}
				p {color:blue;}
			</style>
	  </head>
	  
	2.<link rel="stylesheet" type="text/css" href="mystyle.css">
	
	3.<h1 style="text-align:center;">Center-aligned heading</h1>
	
	
6.Table

	<table border="1">
		<tr>
			<th>Header 1</th>
			<th>Header 2</th>
		</tr>
		<tr>
			<td>row 1, cell 1</td>
			<td>row 1, cell 2</td>
		</tr>
		<tr>
			<td>row 2, cell 1</td>
			<td>row 2, cell 2</td>
		</tr>
	</table>
	
	
7.list

	无序和有序
	
	<ul>
		<li>Coffee</li>
		<li>Milk</li>
	</ul>
	
	
	<ol>
		<li>Coffee</li>
		<li>Milk</li>
	</ol>
	
	
8.div span

	大多数 HTML 元素被定义为块级元素或内联元素。
	块级元素在浏览器显示时，通常会以新行来开始（和结束）。
	实例: <h1>, <p>, <ul>, <table>
	
	
9.form

	<form>
		 <input type="text" name="firstname"><br>
		 <input type="password" name="pwd">
		 
		 <input type="radio" name="sex" value="male">Male<br>
		 <input type="radio" name="sex" value="female">Female
		 
		 <input type="checkbox" name="vehicle" value="Bike">I have a bike<br>
		 <input type="checkbox" name="vehicle" value="Car">I have a car 
		 
		 <input type="submit" value="Submit">
	</form>

	<form>	定义供用户输入的表单
	<input>	定义输入域
	<textarea>	定义文本域 (一个多行的输入控件)
	<label>	定义了 <input> 元素的标签，一般为输入标题
	<fieldset>	定义了一组相关的表单元素，并使用外框包含起来
	<legend>	定义了 <fieldset> 元素的标题
	<select>	定义了下拉选项列表
	<optgroup>	定义选项组
	<option>	定义下拉列表中的选项
	<button>	定义一个点击按钮
	<datalist>New	指定一个预先定义的输入控件选项列表
	<keygen>New	定义了表单的密钥对生成器字段
	<output>New	定义一个计算结果






10.标签使用情况

	较多 html body style a img hn div span  ul ol li p  br  
	较少 table hr 
	
	
	
ref: http://www.runoob.com/html/html-quicklist.html














html5


1.新特性：

	用于绘画的 canvas 元素
	用于媒介回放的 video 和 audio 元素
	对本地离线存储的更好的支持
	新的特殊内容元素，比如 article、footer、header、nav、section
	新的表单控件，比如 calendar、date、time、email、url、search
