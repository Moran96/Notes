## 1. 浏览器后退debug适配全局（对于仿路由结构）

#### 1.1. 添加函数：

- windowGoBack()  在单元内跳转时添加一层history，并添加'popstate'侦听事件,在检测到浏览器后退时执行goback回调
- unknownActMethod()  处理未定义激活方式

#### 1.2. 修改函数：

- goback()  添加熔断代码，预防用户意外操作; 此处注意`viewStack`取名可能不同/注意栈底字符标识名

- beforeDestroy() 清除浏览器'popstate'事件，使其只在当前vue对象生效

#### 1.3. 为每个 `type='list'` 按钮的点击事件添加 `windowGoBack()`

#### 1.4. 注意事项

- 注意不要根据项目url寻找对应vue对象(项目中存在重名但未被使用的vue单元)
- 正确方式：url --> router.js路由列表 --> 组件调用文件

## 2. 浏览器后退debug适配全局（对于锁链结构）

#### 2.0 方案变化

- 锁链结构的内层vue按照仿路由方式解决，最外层vue按下文新的解决方案执行.
- 对于最外层，由于无内层结构的点击入口，故直接操作生命周期函数 created/beforeDestroy.
- created() 添加浏览器 `popstate` 侦听事件， 回调为 `myGoback`
- beforeDestroy() 注销窗口侦听事件

#### 2.1. 添加函数(最外层)

- myGoback() 即在原始代码的`goBack`函数外套一层`if`结构,判断当前层级，若为中间层则执行外部回退
- addHistory() 历史记录压栈，添加在method内

#### 2.3. 为每个 `type='list` 按钮添加 `addHistory()`方法

## 3. 适配进度&路由对应vue组件

|业务层次|文件路径|结构|关联组件|完成情况|其他|备注|
|---|---|---|---|---|---|---|
|翻译库-语种库|`./views/translation/languageLibrary`|仿路由|0|Y|
|翻译库-互译库|`./views/translation/translationHistory` `./views/translation/translationLibrary`|锁链|1|Y||
|翻译库-拍照翻译库|`./views/translation/pictureHistory` `./views/translation/pictureTranslation`|锁链|1|Y|
|翻译库-录音翻译库|`./views/translation/recordHistory` `./views/translation/recordTranslation`|锁链|1|Y|
|翻译库-语言学习库|`./views/translation/learningLibrary` `./views/translation/learningLanguage`|锁链||1|Y|
|翻译库-离线包管理||无||Y||
|翻译库-默认常用语种||无||Y||
|翻译库-默认常用语速||无||Y||
|语音助手模块||无||Y||
|客户管理-激活列表||单层后期会转多层||Y|后期以仿路由模式实现|
|客户管理-客户列表|`./views/customerList/index`|单层||Y||
|客户管理-功能列表||||Y||
|客户管理-属性管理||||Y||
|用户反馈模块||无||Y||
|菜单管理-账号管理||无||Y||
|菜单管理-角色权限管理||无||Y||
|菜单管理||数据驱动||Y||
