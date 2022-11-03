## javascript学习
参考： https://www.w3docs.com/learn-javascript.html


### Limitations of In-browser JavaScript

The capabilities of JavaScript are limited for the purpose of keeping the user’s safety. With it, an evil web page can’t access private information or harm the user’s data.

Here are some examples of such restrictions:

+ JavaScript has no direct access to OS functions. It can’t read and write arbitrary files on the hard disc, copy or execute them.
+ Different windows/tabs don’t recognize each other. JavaSCript from one page is not able to access the other one, in case they are from different sites. It’s known as “Same Origin Policy”.
+ JavaScript allows communication over the net to the server from where the page comes from. But, its capability of receiving data from the other site is prohibited. That’s a safety limitation.(**所以如何跨域呢**)


### JavaScript has a lot of advantages like:

+ Less server interaction
+  Immediate feedback to the visitors
+   Increased interactivity
+   Richer interfaces

### DOM standard

JavaScript usually doesn’t use cryptic numeric codes for representing node types. Many other parts of the DOM interface also feel complicated and alien. **The reason is that the DOM wasn’t designed only for JavaScript.**
Quite, it tries to be a language-neutral interface, which can be used in other systems as well—not just for HTML but also for XML - a generic data format with an HTML-like syntax.



### Ways to Finding HTML Elements

Now you know what DOM document is, so we can start getting our first HTML elements. There are a lot of ways to do so using the Javascript DOM, here are the most common:

+ Get element by ID

We use `getElementById()` method to get a single element by its id. Take a look an example:
```js
let title = document.getElementById(‘title-id’);
```

+ Get elements by class name 

Using the `getElementsByClassName()` method we can also get more than one object. The method returns an array of elements.
```js
let elements = document.getElementsByClassName(‘list-elements’);
```
We get all the items with the class list-elements then save them into a variable.

+ Get element by tag name

We get our elements by tag name using the `getElementsByTagName()` method.

All element nodes include a `getElementsByTagName()` method, it collects all elements with the given tag name which we call descendants (direct or indirect children) of that node and returns them as an array-like object.
```js
let paragraphsEl = document.getElementsByTagName(‘p’);
```
As so see we get all p elements of our HTML document and save them into a variable.


+ Get element by CSS Selectors

If you want to find all HTML elements that match a specified CSS selector, use the `querySelectorAll()` method.
```js
let elements = document.querySelectorAll("h1");
```
When we want to find some specific node in the document, we can’t just reach it by begining at document.bodydocument.body and following a fixed path of properties.

One of the reasons is that text nodes are created for the whitespace between nodes. The example document’s `<body>` tag doesn’t have just 3 children (`<h1>`, `<h2>` and `<p>` elements) but has 7: those 3, plus the spaces before, after, and between them.

### ways to Changing HTML Elements

+ change cotent of HTML element
With HTML DOM we can change the content and style of an HTML element by changing its attribute. We use innerHTML attribute for changing the content of an HTML element.
```javascript
document.getElementById(“#title”).innerHTML = “Welcome to W3Docs!!”;
```

+ Adding and deleting elements

For adding elements we need to create a div element using the `createElement()` method which gets a tagname and saves it into a variable. After we just need to give it some content and insert it into our DOM document.
```js
let p = document.createElement(‘p’);
let txt = document.createTextNode("some text");
p.appendChild(txt);
p.setAttribute("id", "myp");
let div = document.getElementById("mydiv");
div.appendChild(p)
```
using `removeChild()` to remove element from it's parents.
```js
let p = document.getElementById("myp");
p.parentNode.removeChild(p);
```


### use strict 
The "use strict" directive is not a statement, but a literal expression, which was ignored by many earlier versions of JavaScript. The main aim of "use strict" is to indicate that the code should be executed in "strict mode". Almost all modern browsers support "use strict". **When new browser sees the keyword "use strict" it turns itself into strict mode operating.**


We declare strict mode after adding `"use strict"` to the beginning of a function or a script. When it declared at the beginning of a script, it has global scope, which means that all code in the script will execute in strict mode.


### data Types

The newest ECMAScript(ES6) standard defines 8 data types: 7 of them are Primitive.

+ Numbers: 10, 5.4, etc.
+ String: “Welcome to W3Docs” etc.
+ Boolean: Represents a logical operation and can have two values: true or false.
+ Symbol: This is for unique identifiers.
+ BigInt: It is for integer numbers of arbitrary length.
+  Null: Has only one value: null.
+  Undefined: A variable which hasn’t been assigned a value.

And one special type:

+ Object:The most important data-type for modern JavaScript.


### Variable declaration in JavaScript
As we mentioned, there are 3 ways to declare a variable in JavaScript: `let`, `const` and `var`. 

+ `var` 变量定义可以在后面定义，因为，js特性，不管变量在哪定义，执行的时候都是先声明变量。再执行语句。但是，var在定义之前被访问了，会得到一个undefined值，除非在访问之前初始化。
+ `let` 定义的变量只能定义后才能访问，不像`var`那样子。所以推荐以后都用let定义变量。这样容易提前发现程序的错误。。

+ `const`和`let` 基本一样，唯一区别就是，声明的变量不可修改。即常量。所以推荐如下：
  It is a good practice for declaring your constants in uppercase, which will help programmers to separate the constants from other variables in the program.

```js
const VARNAME = “Welcome to W3Docs”; // initialized with a string

const MYBIRTHDAY = '19.03.1986';
MYBIRTHDAY = '04.05.2003'; // error, can't reassign the constant!
```
We can declare variables by using the `var`, `let`, or `const` keywords.

+ `let` is a modern variable declaration.
+ `var` is an old variable declaration.
+ `const` is similar to let, but the value of the variable can’t be changed.

It’s important to name variables in a way that allows us to easily understand what’s inside them.

### BigInt 
 was added to the language not long ago and it represents integers of **arbitrary** length. A BigInt is created by added n to the end of an integer literal:
```js
const bigint = 8562323159475639012345678901234567890n;
const sameBigint = BigInt("8562323159475639012345678901234567890");
const bigintNumber = BigInt(10); // same as 10n
```

### String

We use strings for storing text. In JavaScript, strings can’t be changed, and they must be inside of either double or single quotes.

There are 3 types of quotes in JavaScript:

```
Double quotes:"Welcome".
Single quotes: 'Welcome'.
Backticks: `Welcome`.
```
Double and single quotes are “simple” quotes, practically there is no difference between them in JavaScript. Backticks are “extended functionality” quotes that allow us to embed variables and expressions into a string by wrapping them in ${…}
例如
```js
let a = BigInt("1289437291457398247032094023975907932094803284089");;
console.log(`type=[${typeof(a)}], value=[${a}]`);
```

第三种用于字符串的格式化，非常好用

Note:
> The string with zero "0" is true, as some languages (PHP) treat "0" as false. But in JavaScript, a non-empty string is always true.


### String concatenation
使用 `+` 拼接字符串
> If one of the operands is a string, the other one is transformed to a string as well:

### == 比较符
The equality operator (a == b) **converts the operands if they are not of the same type**, then applies strict comparison. If both operands are objects, JavaScript compares internal references which are **equal when operands refer to the same object in memory**.
即： 如果比较的是 对象(object)。则判断他们是不是同一个对象，是的话则返回true。
比如：
```js
let n = {a: 1, b: 2};
let m = {a: 1, b: 2};
m == n; //  will be false.

let n = {a: 1, b: 2};
let m = n;
m == n; // will be true.
```
### Comparison of different types

For comparing values of different types, JavaScript converts the values to numbers.

For boolean values, true becomes 1, false becomes 0.
例如
```js
true == 1 // will be true.
true == 3 // will be false.
```

### null 和 undefined 比较

```js
null === undefined // will be false.
null == undefined // will be true.
```

### The Difference between == and ===

JavaScript has two visually similar, but very different ways to test equality:

== (Double equals operator): the equality or abstract comparison operator

=== (Triple equals operator): the identity or strict comparison operator

Here are the differences between == and ===:

before showing comparison == converts the variable values of the same type;
    === does not do any type conversion and returns true only if both values and types are identical for the two variables being compared.

总结： 建议使用 === 比较，必要的时候通过 String() 或者 Numer() 函数手动转，而不使用自动的转换。



奇怪的地方
```js
null >= 0  // true
null > 0    // false
//但是
null == 0   // false.
```

原因： 
> The main reason is that an equality check == and comparisons > < >= <= work in a different way: comparisons convert null to a number, treating it as 0. That’s the reason why (3) null >= 0 is true and (1) null > 0 is false.

> But on the other hand, the equality check == for undefined and null is defined without any conversions. They equal each other and don’t equal anything else, that’s why (2) null == 0 is false.


### result = value1 || value2 || value3;

The || (OR) operator executes the following things:

+ Evaluates operands from left to right.
+ For each operand, converts it to boolean. In case the result is true, it stops and returns the original value of that operand.
+ If all operands are false, it returns the last operand.

A value is returned in its initial form, without any changes.

### result = value1 && value2 && value3;

The AND && operator makes the following:

+ Asses operands from left to right.
+ Converts it to a boolean for each operand. In case the result is false, it stops and returns the original value of that operand.
+ If all operands were truthy, it returns the last operand.

例如：
```js
let a = 3 && 4 && 5; // a will be number 5
```



### 小技巧
转换数据到bool类型的两种方式
```js
!!(expr)
Boolean(expr)
```


### ? 三元操作符使用建议
The main purpose of the question mark operator is to return one value or another, it depends on its condition. So use it for exactly that, when you need to execute different branches of code.







