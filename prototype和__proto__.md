### ```prototype ```和```__proto__```

###### 区别

```prototype```是函数才有的属性

```__proto___```是每个对象都有的属性

大多数情况下，```__proto__```可以理解为“构造器的原型”, 即```__proto__ === constructor.prototype```

例:

```javascript
let a = {}
console.log(a.prototype); // undefined
console.log(a.__proto__); // Object{}

let b = function(){}
console.log(b.prototype); // b{}
console.log(b.__proto__); //function(){}
```

---

###### ```__proro__```属性指向谁

```javascript
/* 字面量方式 */
let a = {};
console.log(a.constructor); //function Object(){[native code]} (即构造器Object）
console.log(a.__proto__ === a.constructor.prototype); //true

/* 构造器方式 */
let A = function (){}; let a = new A();
console.log(a.constructor); // function(){}（即构造器function A）
console.log(a.__proto__ === a.constructor.prototype); //true

/* Object.create()方式 */
let a1 = { a:1 } 
let a2 = Object.create(a1);
console.log(a2.constructor); //function Object() { [native code] } (即构造器Object)
console.log(a2.__proto__ === a1); // true 
console.log(a2.__proto__ === a2.constructor.prototype); //false
```

---

###### 原型链

```__proto___```是任何对象都有的属性，而javascript里万物皆对象，所以形成一条```__proto__```连起来的链条，递归访问```__proto__```必须最终到头，并且值是null

```javascript
let A = function(){};
let a = new A();
console.log(a.__proto__); //A {}（即构造器function A 的原型对象）
console.log(a.__proto__.__proto__); //Object {}（即构造器function Object 的原型对象）
console.log(a.__proto__.__proto__.__proto__); //null
```

