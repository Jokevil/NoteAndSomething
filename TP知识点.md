---
title: TP知识点 
tags: 注意事项,thinkphp
grammar_cjkRuby: true
---

### 关于Model层的 数据表关联
一对一关联   hasOne()
一对多关联	hasMany('关联模型的名字','外键名')
多对一关联   belongTo()
````markdown
	Model层
			User.php
				class User extends Model
					{
   					 protected $pk = 'id';  //设置主键

    				public function tie(){   //方法名自定义
        				    return $this->hasMany('Tiezi','id');     
							//一个user 对应多个tiezi  
							//此时将User表的主键id 当做外键和Tiezi 关联
    				}
    				public function comments()
   					 {
        					return $this->hasMany('Comment','id');
    				}
					}
					
			Tiezi.php
				class Tiezi extends Model
				{
    					protected $pk = 'tiZiId';    

    					public function user()
    					{
        					return $this->belongsTo('User','id');
							//一个tiezi 只属于一个user   一对一关联
							//所以此时是 Tiezi的主键tiZiId  和 User的主键id 关联
    					}
    					public function comments()
    					{	
        					return $this->hasMany('Comment','tid');
   						 }
				}
````


