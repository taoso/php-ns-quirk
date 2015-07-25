# PHP namespace quirk

Let's define three class, `Lv\Foo`, `Lv\Common\Foo` and  `Lv\Bar` in `Foo.php`, `CommonFoo.php` and `Bar.php`.

The `Lv\Bar` extends the  `Lv\Common\Foo` by using `use Lv\Common\Foo` and extends `Lv\Common\Foo`'s alias `Foo`.

And then, in `app.php`, if we make an instance of `Lv\Foo`, and then try to make an instance of `Lv\Bar`, the bellow error will be reported,

```
PHP Fatal error:  Cannot use Lv\Common\Foo as Foo because the name is already in use in ...
```

The expected result should be that the `Lv\Common\Foo`'s *alias* `Foo`, which is in the script `CommonFoo.php` with the `Lv` namespace will not confilict the `Lv\Foo`.
