常
量
//ES5常量写法
Object.defineProperty(typeof global === "object" ? global : window, "PI", {
    value:        3.1415926,
    enumerable:   true,
    writable:     false //赋值不能改变
});
// ES6 声明常量的语法
const PI = 3.1415926;
箭头函数 this指向
//使用箭头函数，this指向不同！！
let Fn = function() {
    this.a = 'a';
    this.b = 'b';
    this.c = {
        a: 'a+',
        b: () => this.a,
        c: () => this.c.a
    }
}
console.log(new Fn().c.b()); //a
console.log(new Fn().c.c()); //a+

let Fn=function(){
    this.a='a';
    this.b='b';
    this.c={
        a:'a+',
        b:function(){
            return this.a
        }
    }
}
console.log(new Fn().c.b()); //a+
默认参数
// ES5 默认参数
function f(x, y, z) {
    if (y === undefined)
        y = 7;
    if (z === undefined)
        z = 42;
    return x + y + z;
};
console.log(f(1));//50
// ES6 默认参数
function checkParameter(){
    throw new Error('can\'t be empty!')
};

function f(x = checkParameter(),y = 7,z = 42){
    return x + y + z
}
console.log(f(1));
//捕捉异常
try {
    console.log(f(1));//50
    console.log(f());
} catch (e) {
    console.log(e);
}
可变参数（求和）
// ES5 可变参数
function f(){
    var a = Array.prototype.slice.call(arguments);
    var sum = 0;
    a.forEach(function(item){
        sum+=item*1;
    })
    return sum;
}
console.log(f(1,2,3));
// ES6 可变参数
function f(...a) {
    var sum = 0;
    a.forEach(item => {
        sum += item * 1
    });
    return sum;
}
console.log(f(1,2,3));
合并数组
// ES5合并数组
var params = [ "hello", true, 7 ];
var other = [ 1, 2 ].concat(params);
// ES5合并数组
var params = [ "hello", true, 7 ];
var other = [ 1, 2, ...params ]; // [ 1, 2, "hello", true, 7 ]
分割字符串
// ES5 分割字符串
var str = "foo";
var chars = str.split(""); // [ "f", "o", "o" ]
// ES6 分割字符串
var str = "foo"
var chars = [ ...str ] // [ "f", "o", "o" ]
代理
// ES3
var Person = function() {
    let data = {
        name: 'es3',
        sex: 'male',
        age: 15
    };
    this.get = function(key) {
        return data[key];
    }
    this.set = function(key, value) {
        if (key !== 'sex') {
            data[key] = value
        }
    }
}
// 声明一个实例
var person = new Person();
// 读取姓名，性别，年龄
console.table({name: person.get('name'), sex: person.get('sex'), age: person.get('age')});
// 修改姓名
person.set('name', 'es3-cname');
console.table({name: person.get('name'), sex: person.get('sex'), age: person.get('age')});
// 修改性别
person.set('sex', 'female');
console.table({name: person.get('name'), sex: person.get('sex'), age: person.get('age')});
// ES5
var Person = {
  name: 'es5',
  age: 15
};
Object.defineProperty(Person, 'sex', {
  writable: false,
  value: 'male'
});
// 读取姓名，性别，年龄
console.table({name: Person.name, sex: Person.sex, age: Person.age});
try {
  // 修改姓名、修改性别
  Person.name = 'es5-cname';
  Person.sex = 'female';
} catch (e) {
  console.log(e);
}
console.table({name: Person.name, sex: Person.sex, age: Person.age});
// ES6
let Person = {
    name: 'es6',
    sex: 'male',
    age: 15
}    
let proxy = new Proxy(Person, {
    get(target, key) {
        return target[key];
    },
    set(target, key, value) {
        if (key !== 'sex') {
            target[key] = value;
        }
    }
});
// 读取姓名，性别，年龄
console.table({name: proxy.name, sex: proxy.sex, age: proxy.age});
// 修改性别
try {
    proxy.sex='female';
} catch (e) {
    console.log(e);
}
console.table({name: proxy.name, sex: proxy.sex, age: proxy.age});
