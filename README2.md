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


```