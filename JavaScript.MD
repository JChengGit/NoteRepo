### 变量

```js
// 连续定义
let user = 'John', age = 25, message = 'Hello';

// 常量
const myBirthday = '18.04.1982';

// js是动态类型
// 特殊数字
let a = Infinity, b = -Infinity, c = NaN;

// 字符串格式化
let name = "John";
let greeting = `Hello ${name}` // Hello, John!;

// 查询类型
typeof xxx
```

### 类型转换

```js
String(123)
Number("123")
Boolean(NaN)
```

### 运算

```js
let s = "my" + "string";  // mystring
alert( '1' + 2 ); // "12"
alert( 2 + '1' ); // "21"
alert( 6 - '2' ); // 4, converts '2' to a number
alert( '6' / '2' ); // 3, converts both operands to numbers

let apples = "2";
let oranges = "3";
// 在二元运算符加号起作用之前，所有的值都被转化为了数字
alert( +apples + +oranges ); // 5

// 三元运算符
let result = condition ? value1 : value2

// JavaScript 中有四个逻辑运算符：||（或），&&（与），!（非），??（空值合并运算符）。
```

### 循环

```js
while (condition) {
  // 代码
  // 所谓的“循环体”
};

do {
  // 循环体
} while (condition);

// for 循环的任何语句段都可以被省略
for (begin; condition; step) {
  // ……循环体……
}

for (key in object) {
  // 对此对象属性中的每个键执行的代码
}

// 标签是在循环之前带有冒号的标识符，语句跳出循环至标签处
labelName: for (...) {
  break;
  ...
}
```

### Switch

```js
switch (a) {
  case 3:
    alert( 'Too small' );
    break;
  case 4:
    alert( 'Exactly!' );
    break;
  default:
    alert( "I don't know such values" );
}
```

### 箭头函数

```js
let func = (arg1, arg2, ..., argN) => {
    // expression
};
```

### 对象

```js
let user = {
  name,  // 与 name:name 相同
  age: 30
};

// 浅拷贝
Object.assign(dest, [src1, src2, src3...])
// 深拷贝
const _ = require('lodash');
let deepCopyObj = _.cloneDeep(obj);

// 构造
function User(name) {
  this.name = name;
}
let user = new User("Jack");

// 可选链?.  其它变体：?.()  ?.[]
let user = {}; // user 没有 address 属性
alert( user?.address?.street ); // undefined（不报错）
delete user?.name; // 如果 user 存在，则删除 user.name
```





### TODO

函数定义

数据类型和强制类型转换

Promise

this

箭头函数

回调

异步

面向对象

undefined null NaN
