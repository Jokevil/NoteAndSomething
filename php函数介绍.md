---
title: php函数介绍 
tags: 新建,模板,小书匠
grammar_cjkRuby: true
---


### json_encode  json_decode
**注意:**  json只接受utf-8编码的字符，所以json_encode()的参数必须是utf-8编码，否则会得到空字符或者null
1.PHP支持两种数组
```markdown
	$arr1 = Array('one', 'two', 'three');
	$arr = Array('1'=>'one', '2'=>'two', '3'=>'three');
```
2.JS不支持关联数组
3.对两种数组的编码为
```markdown
	echo json_encode($arr);   // ["one","two","three"]
	echo json_encode($arr);


### serialize   unserialize
string serialize ( mixed $value )
这有利于存储或传递 PHP 的值，同时不丢失其类型和结构，**方法和属性**。


### 魔术方法   __xx()
__toString() :用于一个类被当成字符串时应怎样回应

__invoke() :当尝试以调用函数的方式调用一个对象时，会被自动调用