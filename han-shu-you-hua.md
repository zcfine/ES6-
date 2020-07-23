函数参数设置默认值

```js
//es5
function add(a, b) {
    // 判断b是否为空，为空就给默认值1
    b = b || 1;
    return a + b;
}
// 传一个参数
console.log(add(10));

//es6
function add2(a, b = 1) {
    return a + b;
}
console.log(add2(20));
```

不定参数

```js
function fun(...values) {
    console.log(values.length)
}
fun(1, 2)      //2
fun(1, 2, 3, 4)  //4
```

箭头函数

```js
//es5
let sum = function (a, b) {
    return a + b;
}

//es6
let sum2 = (a, b) => a + b;
```

箭头函数+解构

```js
const person = {
    name: "jack",
    age: 21,
    language: ['java', 'js', 'css']
}

//es5
function hello(person) {
    console.log("hello," + person.name)
}
hello(person);

//es6
var hello2 = ({name}) => console.log("hello," +name);
hello2(person);
```



