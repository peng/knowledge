## Object.*

#### 对象的扩展/密封/冻结相关方法

##### Object.preventExtensions()

* 描述：

该方法用来将一个对象变成不可扩展的对象，不可扩展指的是：

> * 不允许为该对象添加新的属性

> * 该对象的原型是不可变的(`immutable`)，即原型不可被修改

但是现有的属性可以：

> * 被删除(使用 `delete` 操作符)

> * 现有属性的值可以被修改

如果给一个不可扩展的对象添加新的属性，会静默失败，如果在严格模式(`'use strict'`)下会抛出一个错误。

* 参数：

期望接收一个对象作为参数，如果不是对象，那么按照 `ES5` 的规范会报错，而 `ES6` 规定把非对象参数将被视为不可扩展的普通对象，不会报错

* 返回值：传入的参数是什么，就返回什么。

##### Object.seal()

* 描述：

该方法用来密封(`seal`)一个对象，被密封的对象将：

> * 不允许为该对象添加新的属性，不允许删除(`delete`)现有属性

> * 该对象的所有属性将变成不可配置的(`non-configurable`)

> * 不允许将该对象的数据属性(`data properties`)转为访问器属性(`accessor properties`)，反之亦然

> * 该对象的原型是不可变的(`immutable`)，即原型不可被修改

但是可以：

> * 修改现有属性的值

* 参数：

期望接收一个对象作为参数，如果不是对象，那么按照 `ES5` 的规范会报错，而 `ES6` 规定把非对象参数将被视为不可扩展的普通对象，不会报错

* 返回值：传入的参数是什么，就返回什么。

##### Object.freeze()

* 描述：冻结一个对象，被冻结的对象将

> * 不允许为该对象添加新的属性，不允许删除(`delete`)现有属性，不允许修改属性的值

> * 该对象的所有属性将变成不可配置的(`non-configurable`)

> * 不允许将该对象的数据属性(`data properties`)转为访问器属性(`accessor properties`)，反之亦然

> * 该对象的原型是不可变的(`immutable`)，即原型不可被修改

* 注意：冻结指的是浅冻结(`freeze is shallow`)，需要递归的冻结一个深对象。

* 参数：

期望接收一个对象作为参数，如果不是对象，那么按照 `ES5` 的规范会报错，而 `ES6` 规定把非对象参数将被视为不可扩展的普通对象，不会报错

* 返回值：传入的参数是什么，就返回什么。

##### Object.isExtensible()

* 描述：检查一个对象是否是可扩展的

* 参数：期望接收一个对象作为参数，如果不是对象，那么按照 `ES5` 的规范会报错，而 `ES6` 规定把非对象参数将被视为不可扩展的普通对象，返回 `false` 不会报错

* 返回值：一个布尔值，如果为 `true` 代表对象可扩展，为 `false` 代表对象不可扩展

* 注意：使用 `Object.preventExtensions`、`Object.seal` 和 `Object.freeze` 处理的对象都是不可扩展的。

##### Object.isSealed()

* 描述：检查一个对象是否是密封的，满足以下条件的对象都属于密封的对象：

> * 使用 `Object.seal` 处理的对象是密封的

> * 使用 `Object.preventExtensions` 处理的 `空对象` 是密封的

> * 如果一个对象所有的属性都是不可配置的(`non-configurable`)，则该对象是密封的

* 参数：期望接收一个对象作为参数，如果不是对象，那么按照 `ES5` 的规范会报错，而 `ES6` 规定把非对象参数将被视为不可扩展的普通对象，返回 `true` 不会报错

* 返回值：一个布尔值，如果为 `true` 代表对象是密封的，为 `false` 代表对象不是密封的

* 注意：使用 `Object.freeze` 处理的对象也是密封的。

##### Object.isFrozen()

* 描述：检查一个对象是否被冻结，满足以下条件的对象都属于被冻结的对象：

> * 使用 `Object.freeze` 处理的对象是被冻结的

> * 使用 `Object.preventExtensions` 或 `Object.seal` 处理的 `空对象` 是被冻结的

> * 如果一个对象所有的属性都是不可写的(`non-writable`)且不可配置的(`non-configurable`)，则该对象是被冻结的

##### `preventExtensions`、`seal` 和 `freeze` 的比较

简单总结如下：

* 使用 `Object.preventExtension` 处理过的对象为不可扩展的，意思是不能够为该对象添加新属性，但已有属性时可写且可配置的

* 使用 `Object.seal` 处理的对象是密封的，在不可扩展的基础上，已有属性都是不可配置的，但可写

* 使用 `Object.freeze` 处理的对象是冻结的，在密封的基础上，不可写

三个方法都是用来限制对象的扩展性的，他们的关系如下：

* 如果一个对象是被冻结(`frozen`)的，那么该对象一定是密封(`seal`)的和不可扩展(`preventExtensions`)的
* 如果一个对象是密封(`seal`)的，那么该对象一定是不可扩展(`preventExtensions`)的

三个方法限制一个对象的强烈程度为：

`Object.freeze` > `Object.seal` > `Object.preventExtension`

---

#### 【ES2022】Object.hasOwn()

* 描述：检查对象是否包含指定的自有属性（不会检查原型链）

* 参数：
    * 第一个参数：要检查的对象
    * 第二个参数：要检查的属性名

* 返回值：`true` 如果对象包含该自有属性，`false` 否则

* 与 `hasOwnProperty` 的区别：
    1. `hasOwn` 是静态方法，不会受到对象上可能存在的同名属性干扰
    2. 对于使用 `Object.create(null)` 创建的对象（没有原型），`hasOwnProperty` 会报错

* 示例：
```js
const obj = { foo: 'bar' };

// 传统方式
obj.hasOwnProperty('foo');  // true

// 新的方式（推荐）
Object.hasOwn(obj, 'foo');  // true

// 处理没有原型的对象
const nullProtoObj = Object.create(null);
nullProtoObj.foo = 'bar';
// nullProtoObj.hasOwnProperty('foo'); // 报错！
Object.hasOwn(nullProtoObj, 'foo');    // true

// 不会检查原型链
obj.toString;  // [Function: toString]
Object.hasOwn(obj, 'toString');  // false（继承自 Object.prototype）
```

#### 【ES2024】Object.groupBy()

* 描述：根据回调函数返回的键将数组元素分组

* 参数：
    * 第一个参数：可迭代对象（如数组）
    * 第二个参数：回调函数，接收 (item, index) 参数，返回用于分组的键

* 返回值：一个对象，键是分组标识，值是对应的元素数组

* 示例：
```js
const inventory = [
    { name: 'apple', type: 'fruit', quantity: 5 },
    { name: 'banana', type: 'fruit', quantity: 2 },
    { name: 'carrot', type: 'vegetable', quantity: 10 },
    { name: 'broccoli', type: 'vegetable', quantity: 3 }
];

// 按 type 分组
const grouped = Object.groupBy(inventory, ({ type }) => type);
// {
//   fruit: [
//     { name: 'apple', type: 'fruit', quantity: 5 },
//     { name: 'banana', type: 'fruit', quantity: 2 }
//   ],
//   vegetable: [
//     { name: 'carrot', type: 'vegetable', quantity: 10 },
//     { name: 'broccoli', type: 'vegetable', quantity: 3 }
//   ]
// }

// 按数量是否充足分组
const stockStatus = Object.groupBy(inventory, ({ quantity }) => 
    quantity > 5 ? 'sufficient' : 'low'
);
// {
//   low: [{ name: 'apple', ... }, { name: 'banana', ... }, { name: 'broccoli', ... }],
//   sufficient: [{ name: 'carrot', ... }]
// }
```

<p class="tip">`Object.groupBy()` 返回的对象使用 `null` 原型，因此没有继承 Object.prototype 的方法</p>

#### 【ES2024】Map.groupBy()

* 描述：与 `Object.groupBy()` 类似，但返回 Map 而不是对象

* 优势：
    1. 可以使用任意类型的值作为键（不仅仅是字符串和 Symbol）
    2. 适合需要复杂键的场景

* 示例：
```js
const items = [1, 2, 3, 4, 5];

// 使用对象作为键
const grouped = Map.groupBy(items, (num) => {
    return num % 2 === 0 ? { type: 'even' } : { type: 'odd' };
});

// grouped 是 Map，键是对象 { type: 'even' } 和 { type: 'odd' }
```

---

## ES2020+ 其他新特性

### BigInt - 大整数

* 描述：表示任意精度的整数，突破了 Number.MAX_SAFE_INTEGER (2^53 - 1) 的限制

* 创建方式：
```js
const big = 9007199254740993n;           // 在整数后加 n
const same = BigInt(9007199254740993);   // 使用构造函数
```

* 注意事项：
    * BigInt 和 Number 不能直接混合运算
    * 比较运算符可以混用（`1n == 1` 为 true，`1n === 1` 为 false）

### 空值合并运算符 (??)

* 描述：当左侧为 `null` 或 `undefined` 时，返回右侧值

```js
const value = 0;
value || 'default';   // 'default'（0 是 falsy）
value ?? 'default';   // 0（0 不是 null/undefined）

null ?? 'default';    // 'default'
```

### 可选链操作符 (?.) 

* 描述：安全地访问嵌套对象属性

```js
const user = { profile: { name: 'John' } };

// 使用可选链
user.profile?.address?.city;  // undefined（不报错）
user.profile?.name;           // 'John'
```

### globalThis

* 描述：统一的方式访问全局对象

```js
globalThis === window;     // true（浏览器）
globalThis === global;     // true（Node.js）
```

### WeakRef & FinalizationRegistry

* 描述：弱引用，不会阻止垃圾回收

```js
// 弱引用对象
let target = { data: 'valuable' };
const ref = new WeakRef(target);

// 获取引用（可能返回 undefined）
const obj = ref.deref();

// 清理回调注册表
const registry = new FinalizationRegistry((heldValue) => {
    console.log(`Object was garbage collected`);
});
registry.register(target, 'metadata');
```
