```javascript
 // 代码顺序执行
 onClickExport () {
      this.maxHeight = 9999
      console.log('export:')
      this.$utils.downloadPngById('gantt-body', () => {
          console.log('reset maxheight')
          this.initMaxheight()
      })
  }
```
```javascript
 // Vue.nextTick() 异步执行
 onClickExport () {
      this.maxHeight = 9999
      this.$nextTick(function () {
          console.log('export:')
          this.$utils.downloadPngById('gantt-body', () => {
              console.log('reset maxheight')
              this.initMaxheight()
          })
      })
  }
```
```javascript
  // 监听子组件响应式数据maxHeight变化
  watch: {
      ...
      maxHeight: function () {
          console.log('maxHeight changed in gantt-model.')
      }
  }
```

#### 1. 代码顺序执行 截图工作在 `maxHeight` 更新前执行 未达到预期效果

- log

![noNext.png](quiver-image-url/63BAACFEA1C7D1D8A97F9DB5195D9AFF.png =574x145)

- 效果

![noNextExport.png](quiver-image-url/2935D4EFF29D90958A7E6FF76F0ED7D5.png =1591x602)

#### 2. 使用 `Vue.nextTick()` 异步执行 截图工作在 `maxHeight` 更新后执行 达到预期效果

- log

![useNext.png](quiver-image-url/DA5B296A27BB44537AF6850C1E9C1F9C.png =555x161)

- 效果

![useNextExport.png](quiver-image-url/AA943F96717315A650818A93FA5FA5D8.png =1580x759)