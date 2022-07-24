ES6使用总结

- 从var到let,const  
var 存在变量提升的特点，可以重复声明变量，不支持块级作用域，不能用于定义常量，不指定情况下默认为undefined  

let只在代码块内有效，const的值不可改变，在声明的时候就要初始化。先声明，后使用。它们都是块级作用域。

- 变量解构赋值
何为解构：ES6允许按照一定模式，从数组和对象中提取值，对变量进行赋值，这被称为解构(Destructuring)  

支持数组，对象，字符串，数值和布尔，函数参数  

对应变量声明语句，解构模式不能使用圆括号（）
解构的例子：  
```
let [a,[b,c]] = [10,[20,30]]; //数组
let [x,,y] = [10,20,30]; // 解构部分
let {age, name} = {name: 'zhang', age: 22}; // 解构对象
let {age:a, name:nm} = {name: 'zhang', age: 22}; //增加别名
const [a,b,c,d,e] = 'hello'; //字符串解构
```
解构赋值时，只要等号右边的值不是对象或数组，就先将其转为对象。基本类型转包装类型。  

函数的参数，也支持解构赋值  
```
function set({x=0, y=0}={}) {
    return [x,y];
}
set({x:1,y:2});  // [1,2]
set({x:1}); // [1,0]
set({}); // [0,0]
```

- 字符串的扩展增强
增强的字符串，用反引号(`)表示  
有普通字符串的特性，支持定义多行字符串，也可在字符串中嵌入变量（$(varname)）  
如果在模板字符中需要使用反引号，则前面需要用反斜杠转义  
模板字符串之中可以放入js表达式、对象属性、还能调用函数

- 字符串支持的新方法
includes, startsWith, endsWith, repeat, padStart, padEnd, trim, trimStart, trimEnd, match, matchAll  

- 扩展运算符（...）
```
let usr = {name: 'xhang', age: 22};
let usr2 = {...usr}; // 克隆一份独立的

// 数组
let arr = [1,2,3];
let arr2 = [...arr];

// 处理剩余参数
fucntion test(...params) {
    console.log(params);
}
test(1,2,3,4);
```
可用于解构赋值  

- 多进制的表示和处理
0b: 2进制
0o: 8进制
0X: 16进制

Number.parseInt(80, 2);  // 80转为2进制  
Number.isFinite(param);  // param不是数字类型，一律返回false,可用于判断是否为数字  

- 函数参数的默认值
function(uname="lifa") {
    // uname = uname or lifa;
}  

- 箭头函数
var f1 = () =>{
   // 定义了一个箭头函数 
}  

this 怎么理解？

- 数组的扩展
遍历：  
for循环遍历
for...in遍历  
forEach遍历
for...of遍历

如何遍历Map,Set,子串  

新增的方法：  
Array.of // 创建数组  
find，findIndex  // 查找数组成员  
some(),every()  // 检查数组成员是否满足指定的测试  
fill() // 使用指定的元素替换原数组内容

- 增加Set和Map数据结构
new Set([1,2,3,4]);
new Map([['name', 'zhang'],['age', 20]]);

- 对象扩展
let name = "zhang";
let age = 20;
let std = {"name": name, "age": age};
let std2 = {name,age}; // 与上等价  

- 对象新增方法
Object.is(); // 比较两个值是否严格相等  
Object.assign(); // 对象合并；多个源对象有同名属性时，后面的属性会覆盖前面的属性  
Object.getOwnPropertyDescriptors(); // 返回指定对象所有自身属性（非继承）的描述对象。  
Object.keys(),Object.values(),Object.entries() // 键，值，键值对  


- Class语法支持 
```
class Stu {
    constructor(id) {
        this.id = id;
    }  
    toString() {
        return ""+ this.id;
    }
    // 静态方法
    static demo() {
        console.log("hello");
    }
}

// 创建对象
let ent = new Stu(100);
// 调用静态方法
Stu.demo();
// 调用普通类方法
ent.toString();
```

- 类的继承
```
class Person {
    constructor(name) {
        this.name = name;
    }
    toString() {
        return ""+ this.name;
    }
}

class Stu extends Person {
    constructor(name, id) {
        super(name);
        this.id = id;
    }  
    toString() {
        return ""+ this.id;
    }
}

// 继承类的使用
const std = new Stu("zhang", 122);
console.log(std.name, std.id);
std.toString();
```
