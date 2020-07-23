数组解构

```js
let arr = [1,2,3];

//es5
let a = arr[0];
let b = arr[1];
let c = arr[2];

//es6
let [a,b,c] = arr;
```

对象解构

```js
const person = {
    name: "jack",
    age: 21,
    language: ['java', 'js', 'css']
}

//es5
const name = person.name;
const age = person.age;
const language = person.language;

//es6
const { name: abc, age, language } = person;
console.log(abc, age, language)
```

字符串扩展

```js
let str = "hello.vue";
console.log(str.startsWith("hello"));//true
console.log(str.endsWith(".vue"));//true
console.log(str.includes("e"));//true
console.log(str.includes("hello"));//true
```

字符串模板

```js
let age = 18;
let str = `小明今年${age}岁`

function fun() {
    return "这是一个函数"
}
let info = `小明今年${age + 10}了, 我想说： ${fun()}`;
```



