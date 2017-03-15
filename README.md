# ponydep-ncurses

## Packages

Since there have been some breaking changes in ncurses, and RedHat has started packaging the old version in a different package, we're trying to find an easy way to guarantee that installing  `pony-release` RPM will also install the right depencency.

So this project will build two RPMs which provide the same virtual package: `ponydep-ncurses`.  Pony RPMs can depend on that, like so, and whichever of the two is available will be installed:

* ponyc-release (requiring ponydep-ncurses)
  * ponydep-ncurses (a virtual package / capability)
     * ponydep-ncurses-libs-5 (requiring actual ncurses-libs < 6, providing ponydep-ncurses)
     * ponydep-ncurses-libs-5-compat (requiring actual ncurses-compat-libs >= 6, providing ponydep-ncurses)


## References

* the Pony issue discussing [the creation of this](https://github.com/ponylang/ponyc/issues/1208#issuecomment-286281766)
* FPM's [wiki documentation](https://github.com/jordansissel/fpm/wiki)
* a Stack Overflow thread discussing [how RPM did not (or does not?) yet handle weak dependencies](http://unix.stackexchange.com/questions/57524/yum-and-recommended-suggested-packages/57527#57527)
* Travis' [documentation on Bintray deployment](https://docs.travis-ci.com/user/deployment/bintray/)
* Digital Ocean's [notes on package management commands](https://www.digitalocean.com/community/tutorials/package-management-basics-apt-yum-dnf-pkg)
* Digital Ocean's [notes on FPM](https://www.digitalocean.com/community/tutorials/how-to-use-fpm-to-easily-create-packages-in-multiple-formats)
* a tip about [the `rpmrebuild -e -p <rpm_file>` command](http://stackoverflow.com/questions/5613954/extract-the-spec-file-from-rpm-package)),
* [RPM spec file syntax](http://wiki.rosalab.ru/en/index.php/RPM_spec_file_syntax)
* [rpm.org's document on Dependencies](http://rpm.org/user_doc/dependencies.html)
