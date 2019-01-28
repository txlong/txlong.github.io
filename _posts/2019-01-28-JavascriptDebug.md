---
layout: post
title:  "Javascript常用调试技巧"
date:   2019-01-28
categories: random
---

# 日志输出：

```javascript
// 分级输出
console.log('文字信息');
console.info('提示信息');
console.warn('警告信息');
console.error('错误信息');

// 分组输出
console.group('第一个组');
    console.log("1-1");
    console.log("1-2");
    console.log("1-3");
console.groupEnd();

console.group('第二个组');
    console.log("2-1");
    console.log("2-2");
    console.log("2-3");
console.groupEnd();

// 嵌套输出
console.group('第一个组');
    console.group("1-1");
        console.group("1-1-1");
            console.log('内容');
        console.groupEnd();
    console.groupEnd();
    console.group("1-2");
        console.log('内容');
        console.log('内容');
        console.log('内容');
    console.groupEnd();
console.groupEnd();

console.groupCollapsed('第二个组');
    console.group("2-1");
    console.groupEnd();
    console.group("2-2");
    console.groupEnd();
console.groupEnd();

// 表格输出
var table = {
    row1: {
        column1: "aaa",
        column2: "bbb",
        column3: "ccc"
    },
    row2: {
        column1: "aaa",
        column2: "bbb",
        column3: "ccc"
    },
    row3: {
        column1: "aaa",
        column2: "bbb",
        column3: "ccc"
    },
    row4: {
        column1: "aaa",
        column2: "bbb",
        column3: "ccc"
    }
}
console.table(table);

var newTable = [
    ["aa","bb","cc"],
    ["dd","ee","ff"],
    ["gg","hh","ii"],
]
console.table(newTable);
```

```javascript
// 可以在输出的对象、变量前加上提示信息，增加辨识度
var name = "iAnonymous"
console.log("提示语：", name);

// 格式化输出
// %s   字符串输出
// %d   整数输出
// %i   整数输出
// %f   浮点数输出
// %o   打印javascript对象，可以是整数、字符串以及JSON数据

var book = {
    name: "JiuZhangSuanShu",
    price: 23
}
console.log("%s整数部分：%d，带上小数是：%f，来自%o", "圆周率", 3.1415, 3.1415, book);
```

说明：console

# 查看功能

```javascript
// 查看变量
var coder = {
    name: 'iAnonymous',
    bio: 'coding'
}
console.log("console.dir(coder)");
console.dir(coder);
console.dirxml(coder);// 在Chrome中console.dirxml()和console.log()效果相同
```

# 判断输出

```javascript
console.assert(true, "你永远看不见我");
console.assert((function() { return true;})(), "你永远看不见我");

console.assert(false, "你看得见我");
console.assert((function() { return false;})(), "你看得见我");
```

# 计次输出

```javascript
(function () {
    for(var i = 0; i < 3; i++){
        console.count("运行次数：");
    }
})()
```

# 追踪调用堆栈

```javascript
function add(a, b) {
    console.trace("Add function");
    return a + b;
}

function add3(a, b) {
    return add2(a, b);
}

function add2(a, b) {
    return add1(a, b);
}

function add1(a, b) {
    return add(a, b);
}

var x = add3(1, 1);
```

# 计时功能

```javascript
console.time("Chrome中循环1000次的时间");
for(var i = 0; i < 1000; i++)
{

}
console.timeEnd("Chrome中循环1000次的时间");
```

# 自定义样式

```javascript
// 使用%c为打印内容定义样式,再输出信息前加上%c，后面写上标准的css样式，就可以为输出的信息添加样式了
console.log("%cMy stylish message", "color: red; font-style: italic");
```