#### 新建文件夹

`mkdir folderName`
`mkdir pathParent/pathChild`

#### 新建二进制文件

`touch filename`
`touch fileName.xxx`

#### 删除操作

Linux删除目录很简单，使用rm -rf命令即可。

使用规则：`rm -rf pathName`

`-r` 向下递归，不管有多少级目录，一并删除
`-f` 直接强行删除，没有任何提示

示例：
- 删除文件夹实例：
`rm -rf /var/log/httpd`
将会删除/var/log/httpd目录以及其下所有文件、文件夹

- 删除文件使用实例：
`rm -f /var/log/httpd/access.log`
将会强制删除/var/log/httpd/access.log这个文件

- 注意：使用 `rm -rf` 的时候一定要小心，Linux没有回收站。

#### 根据域名查IP
```
liumorandeMacBook-Pro:~ moran$ nslookup www.baidu.com
Server:		114.114.114.114
Address:	114.114.114.114#53

Non-authoritative answer:
www.baidu.com	canonical name = www.a.shifen.com.
Name:	www.a.shifen.com
Address: 14.215.177.39
Name:	www.a.shifen.com
Address: 14.215.177.38

liumorandeMacBook-Pro:~ moran$ nslookup www.hellomoran.cn
;; Got recursion not available from 114.114.114.114, trying next server
Server:		8.8.8.8
Address:	8.8.8.8#53

Non-authoritative answer:
Name:	www.hellomoran.cn
Address: 118.24.124.249
```