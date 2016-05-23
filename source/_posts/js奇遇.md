---
layout: post
title: js奇遇
date: 2016-05-23 23:34:42
categories:
tags:
---

# js数组拷贝
1、 浅拷贝.一个数组的修改会影响到另一个
``` bash
var a = [1, 2, 3, 4],
    b = a;
b[2] = 0;
console.log(a, b);
```
> [1, 2, 0, 4] [1, 2, 0, 4] 

2、concat和slice可以解决以上问题
``` bash
var a = [1, 2, 3, 4],
    b = a.slice(),
    c = a.concat();
b[2] = 0;
c[2] = 0;
console.log(a, b, c);
```
> [1, 2, 3, 4] [1, 2, 0, 4] [1, 2, 0, 4]

3、不过！以上slice和concat并不是使用在所有的数组上都有效(这说明它们的深拷贝只是作用在数组的第一维上)
``` bash
var a = [{name: 'lily', age: 18}, {name: 'lucy', age: 16}],
    b = a.slice(),
    c = a.concat();
b[1].age = 22;
c[1].name = 'bruce';
console.log(JSON.stringify(a), JSON.stringify(b), JSON.stringify(c)); 
```
> [{"name":"lily","age":18},{"name":"bruce","age":22}] 
> [{"name":"lily","age":18},{"name":"bruce","age":22}] 
> [{"name":"lily","age":18},{"name":"bruce","age":22}]

4、那么如何实现数据的真正深拷贝
jQuery就有一个现成的： $.extend
自己扩展 ？


# chrome中类数组对象会自动根据key值进行排序
``` bash
var a = {'23': {name: 'lily', age: 18}, '12': {name: 'lucy', age: 20}};
console.log(JSON.stringify(a));
```
> {"12":{"name":"lucy","age":20},"23":{"name":"lily","age":18}}

