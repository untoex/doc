# HTML

> **Hyper Text Markup Language (超文本标记语言)**

## 标签

> **基础标签**

```scss
<!DOCTYPE html>
//根标签
<html xmlns="XML命名空间" lang="en">
	//元数据
    <head>
		//网页标题
		<title></title>
		//文档级元数据元素
		<meta charset="utf-8">
		<meta name="author" content="作者">
		<meta name="description" content="网页内容描述">
		<meta name="keywords" content="网页关键字">
		//内部样式表
		<style></style>
    </head>
	//网页内容标签
    <body>
		//换行标签
		</br>
		//水平线标签
		</hr>
		//粗体
		<strong></strong>
		//斜体
		<em></em>
		//空格
		&nbsp;
		//普通内联标签
		<span></span>
		//普通块标签
		<div></span>
    <body>
</html>
```

> **表单**
```scss
<form method="提交方式" action="发送地址">
	//method="post" 安全,传输大文件
	//method="get"  不安全(URL可见),高效

	<input name="" type="类型" value="初始值">
		//type="text"     文本  maxlength="最大字符数"
		//type="password" 密码  maxlength="最大字符数"
		//type="submit"	  提交
		//type="image"    图片提交
		//type="reset"    重置
		//type="checkbox" 多选 checked="选中"
		//type="radio"    单选 checked="选中"
		//type="file"     文件
		//type="hidden"   隐藏
		//type="button"   按钮
		//type="color"    颜色
		//type="date"     日期
		//type="time"     时间
		//type="email"    邮箱
		//type="number"   数字 max="最大值" min="最小值"
		//type="range"    滑块 max="最大值" min="最小值"
		//type="tel"      电话
		//type="url"      网址
		//type="search"   搜索
		//readonly 只读
		//disabled 禁用
		//hidden   隐藏
		//required 非空判断
		//pattern  正则表达式
		//placeholder="提示信息" 应用于输入框
		
	//下拉框
	<select name="">
		<option value="" selected></option>
			//selected 默认选择
	</select>
	//文本域
	<textarea name="" cols="列" rows="行"></textarea>
	//增加鼠标可用性
	<label for="id"></label>
</form>
```

> **多媒体**

```scss
//图片标签
<img src="图片地址" alt="文本描述" title="悬停文字" width="宽度" height="高度">
//视频标签
<video src="视频地址" controls autoplay></video>
	//controls 控制元件
	//autoplay 自动播放
//音频标签
<audio src="视频地址" controls autoplay></audio>
```

> **链接标签**

```scss
//链接标签
<a href="链接路径" target="打开窗口"></a> 
	//target="_self"    当前窗口
	//target="_blank"   新开窗口
	//target="_parent"  上层窗口
	//target="_top"     顶层窗口
	//href="#name"      锚链接
	//href="#id"        锚链接
	//href="mailto:邮箱" 邮箱链接
	//href="tel:电话"    电话链接
	//download 下载
//外部样式表
<link rel="stylesheet" type="text/css" href="css地址"/>
//引入脚本
<script type="text/javascript" src=""></script>
```

> **块标签**

```scss
//标题标签
<h1></h1>
<h2></h2>
<h3></h3>
<h4></h4>
<h5></h5>
<h6></h6>

//段落标签
<p></p>
```

> **列表**

```scss
//有序列表
<ol>
    <li>秦时明月汉时关</li>
    <li>万里长征人未还</li>
    <li>但使龙城飞将在</li>
    <li>不教胡马度阴山</li>
</ol>
//无须列表
<ul>
	<li>秦时明月汉时关</li>
    <li>万里长征人未还</li>
    <li>但使龙城飞将在</li>
    <li>不教胡马度阴山</li>
</ul>
//定义列表
<dl>
	<dt>《出塞》</dt>
	<dd>秦时明月汉时关</dd>
    <dd>万里长征人未还</dd>
    <dd>但使龙城飞将在</dd>
    <dd>不教胡马度阴山</dd>
</dl>
```

> **表格**

```scss
<table border="边框">
	<tr>//行rows
		<td colspan="跨列" rowspan="跨行"></td>//列
	</tr>
</table>
```

> **页面结构**

```scss
//网页头部
<header></header>
//导航
<nav></nav>
//网页主体
<main>
	//文章
	<article></article>
	//独立区域
	<section></section>
	//侧边栏
	<aside></aside>
</main>
//网页尾部
<footer></footer>
```

> **内联框架**

```scss
<iframe src="页面地址" name="框架标识名" width="宽" height="高"></iframe>
```

## 全局属性

```scss
id    //选择器;定义唯一标识符
class //选择其;定义类型
```

