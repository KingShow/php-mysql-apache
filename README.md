## php-mysql-apache
mac php环境配置
##hosts修改
```
127.0.0.1    www.test.com
127.0.0.1    wxdc

```
##php.ini
```
cd /etc/  
sudo cp php.ini.default php.ini  
sudo vi php.ini  

另需要配置phpredis 的扩展，下载完成在php.ini,中添加extension=redis.so
session.save_path = "/tmp" 也需要开放
```
##apache 配置
```
cd /etc/apache2/httpd.conf
LoadModule userdir_module libexec/apache2/mod_userdir.so
LoadModule rewrite_module libexec/apache2/mod_rewrite.so
LoadModule php7_module libexec/apache2/libphp7.so

# Virtual hosts 开启虚拟主机配置
Include /private/etc/apache2/extra/httpd-vhosts.conf

DocumentRoot "/Users/oubunfei/Sites"
<Directory "/Users/oubunfei/Sites">
    #
    # Possible values for the Options directive are "None", "All",
    # or any combination of:
    #   Indexes Includes FollowSymLinks SymLinksifOwnerMatch ExecCGI MultiViews
    #
    # Note that "MultiViews" must be named *explicitly* --- "Options All"
    # doesn't give it to you.
    #
    # The Options directive is both complicated and important.  Please see
    # http://httpd.apache.org/docs/2.4/mod/core.html#options
    # for more information.
    #
    Options FollowSymLinks Multiviews Indexes 
    MultiviewsMatch Any

    #
    # AllowOverride controls what directives may be placed in .htaccess files.
    # It can be "All", "None", or any combination of the keywords:
    #   AllowOverride FileInfo AuthConfig Limit
    #
    AllowOverride All

    #
    # Controls who can get stuff from this server.
    #
    Require all granted
</Directory>
DocumentRoot :是项目的指向地址
```
##虚拟主机
```
cd /etc/apache2/extra/httpd-vhosts.conf

<VirtualHost *:80>
    ServerAdmin wxdc
    DocumentRoot "/Users/oubunfei/Sites/wxdc/api/public"
    ServerName wxdc
    ErrorLog "/private/var/log/apache2/error_log"
    CustomLog "/private/var/log/apache2/dummy-host2.example.com-access_log" com$
</VirtualHost>

DocumentRoot:是项目指向
ServerName：访问地址 可以是localhost ,127.0.0.1,或者是自己项目名称
ServerAdmin： 访问地址

```