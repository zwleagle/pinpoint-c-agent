# v0.1.x 和 v0.2.+ 的区别

##  v0.1.x VS. v0.2+

> 为什么要重构pinpoint_c_agent (0.1.x)？

1. 很难支持所有php版本
2. 速度太慢, v0.1.x 挂钩所有函数
3. 不支持ZTS

### 数据线路图

#### v0.1.x

> AOP 基于 zend_excuted_hook

![How does it work](../../images/principle_v0.1.x.png)
#### v0.2+

> AOP 基于 classloader (比如 java-classloaders)

![How does it work](../../images/principle_v0.2.x.png)

#### PHP 版本兼容性

Agent 版本|PHP5.5.x|PHP5.6.x|PHP7.x |php-zts
----|-----|----|-----|---
v0.1.x|✔|✔|✔|✘
v0.2.+|✔|✔|✔|✔

#### PHP 框架

框架|v0.1.x|v0.2+
----|-----|----|
Laravel|✔|✔
ThinkPHP|✔|todo
YII|✔|✔
Workerman|✘|✔
EasySwoole|✘|✔

> 备注

1. 如果您的php应用程序不支持composer(如woredpress、phpwind等)，那么就只能使用v0.1.x。
#### 稳定性

`v0.2+ > v0.1.x`


#### 可维护性(动态地)

```
✔: 不会阻塞用户的应用程序
✘: 阻塞用户的应用程序: 应该重启php-fpm/apache 
```

操作|v0.1.x|v0.2.+
----|-----|----
1.Update plugins(CRUD) |✘|✔ [How to ?](https://github.com/eeliu/php_simple_aop#how-to-reload-all-plugins)
2.Update pinpoint collector|✘|✔
3.Update pinpiont_php.so(pinpoint.so)|✘|✘

### 编者的话

由于人们广泛使用composer，v0.2+是我们长期支持的版本，v0.1.x在未来可能会被淘汰，但是我们可以修复v0.1.x中的一些致命错误。



