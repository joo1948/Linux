
## 인증서가 설치된 이후 작업할 것

### [httpd.conf]
```shell
vi /prd/app/apache/cont/httpd.conf

LoadModule rewrite_module modules/mod_rewrite.so //주석 풀기
Include conf/extra/httpd-vhosts.conf//주석 풀기

<Directory />
  AllowOverride AuthConfig
  Require all denied
</Directory>

DocumentRoot "/prd/app/test~"//실행되는 파일 경로
<Directory "/prd/app/test~"//실행되는 파일 경로>
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
  Options Indexes FollowSymLinks

  #
  # AllowOverride controls what directives may be placed in .htaccess files.
  # It can be "All", "None", or any combination of the keywords:
  #   AllowOverride FileInfo AuthConfig Limit
  #
  AllowOverride AuthConfig

  #
  # Controls who can get stuff from this server.
  #
  Require all granted
</Directory>

``` 
### [httpd-vhost.conf]
```shell
vi /prd/app/apache/conf/extra/httpd-vhost.conf

<VirtualHost *:80>
  DocumentRoot "/prd/app/test~"//실행되는 파일 경로
  ServerName test.~~.com //도메인
  ErrorLog "logs/vhost_error_log"
  CustomLog "logs/vhost_access_log" common
  RewriteEngine On
  RewriteCond %{HTTPS} off
  RewriteRule (.*) https://%{HTTP_HOST}%{REQUEST_URI} [R=301,L]
</VirtualHost>
systemctl restart apache

```
