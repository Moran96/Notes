### null 和 undefined


#### JSON

```javascript
var o = {
    a1: '', // 空字符串
    a2: undefined, // key value 均被过滤
    a3: null // null
}
console.log(JSON.stringify(o)) // {"a1":"","a3":null}
```

#### 函数缺省值

```javascript
function f1(a = 9) {
    console.log(a)
}

f1(undefined) // 9
f1(null) // null
```

#### 内存空间

- 变量声明时，不赋值，默认值为 `undefined`。此时**分配内存空间**
- 将变量赋值为null时，该变量之前被分配的内存空间会被**释放** (释放定时器时常用这种方法)