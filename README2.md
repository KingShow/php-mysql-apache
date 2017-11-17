### mac下安装php扩展phpredis

```
git clone git://github.com/nicolasff/phpredis.git
cd ./phpredis
phpize
make
make install
然后编写ini文件：
vim /opt/local/etc/php5/conf.d/php.ini
内容：
extension=redis.so


```

### 有可能出现的错误提示

```
1,进入php-redis目录，执行phpize报错：
grep: /usr/include/php/main/php.h: No such file or directory
grep: /usr/include/php/Zend/zend_modules.h: No such file or directory
grep: /usr/include/php/Zend/zend_extensions.h: No such file or directory

解决方法：
sudo ln -s /Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX10.9.sdk/usr/include /usr/include
注意：MacOSX10.9.sdk修改成你自己的版本

如果报这个错误 ln: /usr/iclude: Operation not permitted

解决方法

暂时停用系统保护：

按下开机键时即刻按住 command R（“R”字母键），中间的苹果标志及进度条出现后放开按键，等待恢复安装界面和 “OS X 实用工具”
窗口出现后，点击顶部菜单栏的 “实用工具”，在其下拉菜单点选运行 “终端”，在终端闪动字符的位置直接输入“csrutil disable”
并回车，重新启动电脑。


```