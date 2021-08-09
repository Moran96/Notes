### 整体解决思路

- 首先限制改行数据所在容器的宽度和高度, 超出多行后隐藏.
- 点击该位置数据后出现对话框，显示完整信息(高度限制，用垂直方向滚动条提高用户体验)
- 利用 `clipboard` 插件，提供复制至剪贴板功能

### 实现

#### 1. 全局添加插件

```javascript
<script src="assets/js/clipboard.min.js"></script>
```

- `clipboard.min.js` 文件需前往官网下载
- 注意项目有配置按需加载，所以建议将插件加载到 `welcome.html`
- 若在不同文件之间执行复制操作，插件只能复制 `input` 和 `textarea` 内的文本

#### 2. 调整对应数据位置宽度

```javascript
"columnDefs": [
{
    'title': 'ID',
    'width': '6%',
    'targets': 0
},{
    'title': '模号',
    'width': '12%',
    'targets': 1
}
```

- `"columnDefs"` 字段可能有一个或多个，隶属于不同层级表格，需要定位到目标位置

#### 3. 修改该位置样式(折行、按钮点击、消除默认样式、定位)、添加点击事件并传递数据

`js` 文件：

```javascript
$('td:eq(1)', nRow).css({'word-break':'break-all', "position": "relative"})
$('td:eq(1)', nRow).html(`<span class="inner-label-modeltype">${aData[1]}</span> <button class="btn-copy-modeltype" onclick="showMsg('${aData[1]}')"></button>`)
```

```javascript
function showMsg(e) {
    $('#copyModel').modal('show');
    $('#current-model-type').text(e)
}
```

`html` 文件：

```html
<div class="modal my-modal fade" id="copyModel" tabindex="-1" role="dialog" aria-labelledby="myModalLabel" aria-hidden="true">
    <div class="modal-dialog">
        <div class="modal-content">
            <div class="modal-header">
                <button type="button" class="close" data-dismiss="modal">×</button>
                <h4 style="margin: 0;">详情</h4>
            </div>
            <div class="modal-body" style="overflow-y: scroll; text-align: center">
                <textarea rows="15" cols="60" id = "current-model-type" style="resize:none" readonly> 暂无数据 </textarea>
            </div>
            <div class="modal-footer">
                <a class="clipboard btn my-btn btn-primary"  href="javascript:" data-clipboard-target="#current-model-type">复制</a>
                <a href="javascript:" class="btn my-btn btn-primary" data-dismiss="modal">返回</a>
            </div>
        </div>
    </div>
</div>

<script>
    var clipboard = new ClipboardJS('.clipboard');
</script>
```