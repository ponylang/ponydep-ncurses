# ponydep-ncurses

## Packages

Since there have been some breaking changes in ncurses, and RedHat has started packaging the old version in a different package, we're trying to find an easy way to guarantee that installing  `pony-release` RPM will also install the right depencency.

So this project will build two RPMs which provide the same virtual package: `ponydep-ncurses`.  Pony RPMs can depend on that, like so:

* ponyc-release (requiring ponydep-ncurses)
  * ponydep-ncurses (a virtual package / capability)
     * ponydep-ncurses-libs-5 (requiring actual ncurses-libs < 6, providing ponydep-ncurses)
     * ponydep-ncurses-libs-5-compat (requiring actual ncurses-compat-libs >= 6, providing ponydep-ncurses)


## References

* [FPM documentation](https://github.com/jordansissel/fpm/wiki)
* a Pony issue discussing [the motivation for this](https://github.com/ponylang/ponyc/issues/1208#issuecomment-286281766)
* a Stack Overflow thread discussing [how RPM did not (or does not?) yet handle weak dependencies](http://unix.stackexchange.com/questions/57524/yum-and-recommended-suggested-packages/57527#57527)
