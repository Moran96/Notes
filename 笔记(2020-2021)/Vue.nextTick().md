### 官方文档：

> 在下次 DOM 更新循环结束之后执行延迟回调。在修改数据之后立即使用这个方法，获取更新后的 DOM。

#### 测试1：将 `Vue.nextTick` 写在**响应式数据变化前**

```javascript
handleAdd () {
    console.log('ADD begin')
    let len = this.tableData.length
    this.$nextTick(function () {
        console.log('nextTick')
    })
    this.tableData.push({
        id: 1
    })
    console.log('ADD finish')
}
```

控制台打印结果：

```
ADD begin
ADD finish
nextTick
beforeUpdate
updated
```

测试结果：数据更新 -- nextTick回调 -- 视图更新


#### 测试2：将 `Vue.nextTick` 写在**响应式数据变化后**

```javascript
handleAdd () {
    console.log('ADD begin')
    let len = this.tableData.length
    this.tableData.push({
        "id": 1,
    })
    this.$nextTick(function () {
        console.log('nextTick')
    })
    console.log('ADD finish')
},
```

控制台打印结果：

```
ADD begin
ADD finish
beforeUpdate
updated
nextTick
```

测试结果: 数据更新 -- 视图更新 -- nextTick回调

### 总结

> 在下次 DOM 更新循环结束之后执行延迟回调。在修改数据之后立即使用这个方法，获取更新后的 DOM。

- 1. `Vue.nextTick(function () {......})` 参数为一个回调函数，是异步的。即**理论上**内部回调执行的时间点与 `nextTick` 被使用的位置无关。
- 2. 但是由于 `nextTick` 是和响应式数据更新有关的，其被使用的位置是在数据修改前还是数据修改后，会对回调函数的执行时机产生影响。
- 3. 通过测试，当 `nextTick` 在数据修改前被使用，回调发生在数据更新后、视图更新前；在数据修改后被使用，回调发生在视图更新后。完全不同。
- 4. 因此官方文档强调 `在修改数据之后立即使用...`, 一是强调 `修改数据之后`, 而是强调 `立即`; 至于数据修改前使用的情况，被回避了。
- 5. 重新解读官方文档：

> 请在修改数据之后立即使用这个方法, 会在下次 DOM 更新循环结束之后执行延迟回调，获取更新后的 DOM。
> 请不要在修改目标数据前使用这个方法，否则回调会发生在错误的时间点。不要问问什么，问就是不要用、不想多说、请看源码。

- 6. 原理可以查看vue源码，找一下开发者如何实现 `nextTick`，答案就明晰了。