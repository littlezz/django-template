django template 语言简明手册
========================
给有一定基础的同学回忆起template的用法. 


0.布局
-----------
首先需要一个`base.html` , 载入`staticfiles`. 添加`block`

```html
{% load staticfiles %}
<!DOCTYPE html>
<html>
...
{% block content %}

{% endblock %}
...
```

接下来是其他的文件, 注意`{% load staticfiles %}` 只用在base.html里面载入一次即可. 

```template
{% extends 'base.html' %}

{% block content %}
something.
{% endblock %}
```

另外, 你可以使用{{block.super}} 来获得在base.html 中写的内容

```
{% block content %}
{{block.super}}
something.
{% endblock %}
```
通常情况下, 这些文件都在`templates`目录里对应的以应用名称为名字的目录下.  比如`templates/main_app/home.html`

1.链接
------------
假设有一个`main`应用.
设置静态文件:  

	<link rel="stylesheet" href="{% static 'main/css/main.css' %}" type="text/css" />

设置 javascript:  
	
	<script src="{% static 'main/js/jquery-2.1.1.js' %}"></script>

`<a>链接`

	<a href="{% url 'home' %}">go</a>

2.表单
-------
to be continue


