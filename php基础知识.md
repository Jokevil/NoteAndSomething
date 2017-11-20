---
title: php基础知识
tags: 新建,模板,小书匠
grammar_cjkRuby: true
---


欢迎使用 **{小书匠}(xiaoshujiang)编辑器**，您可以通过==设置==里的修改模板来改变新建文章的内容。

## 变量
### 全局变量 定义在函数外   --》要使用global关键词
### 局部变量       函数内定义
$qj1 = '我是全局1，但没有用global关键词';
$qj2= '我是全局2，但没有用global关键词';
eg:
function zdy(){
    global $qj2 ;
    echo $qj2.';
//  此时这句话会报错 找不到变量$qj1   echo $qj1;
}
zdy();

## 静态变量  --》static 关键词 
function z(){
   1. static $m =0;
   2. $m =0;
   $m += 1 ;
}

for($i=0;$i<5;$i++){
  z();
}

1.的运行结果 1 2 3 4 5 
2.的运行结果 1 1 1 1 1

## public private protected区别
public:    可以class内部调用，可以实例化调用。
protected：受保护类型，用于本类和继承类调用，实例化调用报错。
private:   私有类型，只有在本类中使用，不能被继承，实例化调用报错。


## 可变变量  $$kb
该变量的值由另外一个变量的值来确定
eg：
$kb = "trans";
$trans = "i am trans ";
echo $kb.'<br>';  //trans
echo $$kb.'<br>'; //i am trans 

## 变量函数
通过一个变量的值来选择调用哪个函数
function come(){
	echo "来了";
}
function go(){
	echo "走了";
}

$func="come";
$func();    ==>来了

$func="go";
func();    ==>走了




## 逻辑运算符
优先：&& > || > and > xor >or


## 错误控制运算符 @
在错误的表达式前面加@ （只是屏蔽其报错，用于屏蔽无关紧要的错误，并未根本解决错误） 


## 命名规范：

$bian_liang_ming
$gGlobal
$rYingYongBianLiang
$sStaticBianLiang

class LeiMing{
   $mLeiShuXingMing = "";
   function han_shu_ming($canShuMing1,$canShuMing2){
	
   }
}


## 单双引号
### 单引号“所见即所得”原封不动的呈现字符串
### 双引号
如果字符串里有变量会先解析，然后再呈现变量解析后的值
