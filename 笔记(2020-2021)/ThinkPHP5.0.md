### 1. 变量输出

简单变量

```php
/* 在模板中使用 */
Hello,{$name}！
/* 模板编译后的结果 */
Hello,<?php echo($name);?>！
```

数组

```php
$data['name'] = 'ThinkPHP';
$data['email'] = 'thinkphp@qq.com';
$view->assign('data',$data);
--------------------------
Name：{$data.name}
Email：{$data.email}
--------------------------
Name：{$data['name']}
Email：{$data['email']}
```

对象的属性

```
---------------------
Name：{$data:name}
Email：{$data:email}
---------------------
Name：{$data->name}
Email：{$data->email}
```

[参考文献](https://www.kancloud.cn/manual/thinkphp5/125003)

### 2. 内置标签

[内置标签总览](https://www.kancloud.cn/manual/thinkphp5/125016)

#### 2.1. include

- 通常用来传入模版文件
- 可以传入相对路径，支持多个路径
- 可以带参数

```html
<!--test.html-->
<include file='Public::header'/>
<style>...</style>
<body>...</body>
<include file='Public::footer'/>
```

### 2.2. 循环输出

#### 2.2.1. volist

> Volist标签的name属性表示模板赋值的变量名称，因此不可随意在模板文件中改变。id表示当前的循环变量。

```php
{volist name="list" id="vo"}
{$vo.id}:{$vo.name}<br/>
{/volist}
```

#### 2.2.2. foreach

```php
{foreach name="list" item="vo"}
    {$vo.id}:{$vo.name}
{/foreach}
```

#### 2.2.3. for

[for](https://www.kancloud.cn/manual/thinkphp5/125017)

#### 2.2.4. 循环嵌套

```php
{volist name="list" id="vo"}
    {volist name="vo['sub']" id="sub"}
        {$sub.name}
    {/volist}
{/volist}
```