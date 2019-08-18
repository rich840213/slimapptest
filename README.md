# Slimapp Test
Learn RESTful API With PHP &amp; MySQL  
來源作者 https://www.youtube.com/watch?v=DHUxnUX7Y2Y

## 備註
環境 Windows 10 and XAMPP  
API測試工具 Postman  
slimapptest.sql為資料庫備份檔

## 相關設定
**Apache Virtual Hosts**  
修改檔案 xampp\apache\conf\extra\httpd-vhosts.conf
```conf
# Virtual Hosts
#
# Required modules: mod_log_config

# If you want to maintain multiple domains/hostnames on your
# machine you can setup VirtualHost containers for them. Most configurations
# use only name-based virtual hosts so the server doesn't need to worry about
# IP addresses. This is indicated by the asterisks in the directives below.
#
# Please see the documentation at 
# <URL:http://httpd.apache.org/docs/2.4/vhosts/>
# for further details before you try to setup virtual hosts.
#
# You may use the command line option '-S' to verify your virtual host
# configuration.

#
# Use name-based virtual hosting.
#
NameVirtualHost *:80
#
# VirtualHost example:
# Almost any Apache directive may go into a VirtualHost container.
# The first VirtualHost section is used for all requests that do not
# match a ##ServerName or ##ServerAlias in any <VirtualHost> block.
#

<VirtualHost *:80>
    DocumentRoot "E:/xampp/htdocs/slimapptest/public"
    ServerName slimapptest
</VirtualHost>

##<VirtualHost *:80>
    ##ServerAdmin webmaster@dummy-host.example.com
    ##DocumentRoot "E:/xampp/htdocs/dummy-host.example.com"
    ##ServerName dummy-host.example.com
    ##ServerAlias www.dummy-host.example.com
    ##ErrorLog "logs/dummy-host.example.com-error.log"
    ##CustomLog "logs/dummy-host.example.com-access.log" common
##</VirtualHost>

##<VirtualHost *:80>
    ##ServerAdmin webmaster@dummy-host2.example.com
    ##DocumentRoot "E:/xampp/htdocs/dummy-host2.example.com"
    ##ServerName dummy-host2.example.com
    ##ErrorLog "logs/dummy-host2.example.com-error.log"
    ##CustomLog "logs/dummy-host2.example.com-access.log" common
##</VirtualHost>
```
---
**Windows Hosts**  
修改檔案 C:\Windows\System32\drivers\etc\hosts
```txt
# Copyright (c) 1993-2009 Microsoft Corp.
#
# This is a sample HOSTS file used by Microsoft TCP/IP for Windows.
#
# This file contains the mappings of IP addresses to host names. Each
# entry should be kept on an individual line. The IP address should
# be placed in the first column followed by the corresponding host name.
# The IP address and the host name should be separated by at least one
# space.
#
# Additionally, comments (such as these) may be inserted on individual
# lines or following the machine name denoted by a '#' symbol.
#
# For example:
#
#      102.54.94.97     rhino.acme.com          # source server
#       38.25.63.10     x.acme.com              # x client host

# localhost name resolution is handled within DNS itself.
#	127.0.0.1       localhost
#	::1             localhost

127.0.0.1       slimapptest
```
---
**phpMyAdmin密碼設定**  
修改檔案 xampp\phpMyAdmin\config.inc.php 位置大約在18~24行
```php
/* Authentication type and info */
$cfg['Servers'][$i]['auth_type'] = 'cookie';
$cfg['Servers'][$i]['user'] = 'root';
$cfg['Servers'][$i]['password'] = '123456';
$cfg['Servers'][$i]['extension'] = 'mysqli';
$cfg['Servers'][$i]['AllowNoPassword'] = false;
$cfg['Lang'] = '';
```
重新啟動XAMPP Control Panel的Apache and MySQL  
打開XAMPP Control Panel右手邊的Shell輸入
```txt
mysqladmin.exe -u root password 123456
```
---
**Postman測試用JSON (資料新增與修改)**  
```json
{
  "first_name": "aa",
  "last_name": "bb",
  "phone": "123123",
  "email": "abcabc",
  "address": "abcabc",
  "city": "aaabbb",
  "state": "bbbaaa"
}
```
