# PHP 命名空间的奇怪行为

我们定义三个类，分别是`Lv\Foo`，`Lv\Common\Foo`和`Lv\Bar`。

其中，`Lv\Bar`扩展了`Lv\Common\Foo`，而且在`Lv\Bar`的代码中写有`use Lv\Common\Foo`。
请注意这里的`Lv\Foo`和`Lv\Common\Foo`。

那么，在实例化`Lv\Foo`对象之后再试图实例化`Lv\Bar`会报以下错误：
```
PHP Fatal error:  Cannot use Lv\Common\Foo as Foo because the name is already in use in ...
```

这难道是 PHP 的 bug 吗？貌似 HHVM 没有这个问题。

复现方法：
```
php app.php
```
