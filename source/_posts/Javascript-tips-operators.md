---
title: 'Javascript tips: operators'
date: 2020-02-23 11:50:10
tags:javascript
---

# Spread Syntax (扩展语句符 ...)

<font color="red">“..."</font>在JS里表示紧跟其后的表达式，比如数组，字符串等，会做原地展开（expand)。比如，一个函数需要3个参数，而你正好有一个数组包含了三个参数，那么spread syntax可以简化你的代码。

例如：

```javascript
var numbers=[1,2,3]
function multiply(a, b, c){
    return a*b*c;
}

//传统调用
multiply(numbers[0],numbers[1],numbers[2])

//改用spread syntax
multiply(...numbers)
```



* 如果数组的长度小于需要的参数数量，会返回NaN错误。

* 如果数组的长度大于需要的参数数量，则从低位开始截取所需的参数。