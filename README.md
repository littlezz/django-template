django template 语言简明手册
========================
给有一定基础的同学回忆起template的用法. 


0.布局
-----------
首先需要一个`base.html` , 载入`staticfiles`. 添加`block`

```django
{% load staticfiles %}
<!DOCTYPE html>
<html>
...
{% block content %}

{% endblock %}
...
```

接下来是其他的文件, 注意`{% load staticfiles %}` 只用在base.html里面载入一次即可. 

```django
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

设置 javascript, 最好将使用CDN的和本地提供的分类好摆放:  
	
	<script src="{% static 'main/js/jquery-2.1.1.js' %}"></script>

`<a>链接`

	<a href="{% url 'home' %}">go</a>


2.表单
-------
假设表单下有一栏是nickname  

- `{{ form.nickname.labe }}`  

label的名字

- `{{ form.nickname.label_tag }}`   

渲染出一个label标签, `<label for='xxx'>nickname</label>` 这种东西.  

- `{{ form.nickname.id_for_label }}`    

label里面的for属性的值, 多数情况下, 这就是你想要的.用法:    

	<label for="{{ form.nickname.id_for_label }}">custom label</label>

- `{{ form.nickname.html_name }}`

用于input中的name属性的值, 多数情况下, 这就是你想要的.

- `{{ form.nickname.errors }}`

这是你以你应该注意的,提交后错误信息反馈, 多数情况下你用他来判断是否这一栏填写有问题.举例:  

```django
{% if form.nickname.errors %}
	<p>error text</p>
{% endif %}
```


- `{{ form.nickname.value }}`  

对应于value属性

	


