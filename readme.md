# Laravel 4 Vagrant 开发包

一个基于Ubuntu 12.04、PHP 5.4用于开发[Laravel4](http://laravel.com/docs) 的Vagrant包。

## 必要环境

* VirtualBox - 免费的虚拟机 [Downloads](https://www.virtualbox.org/wiki/Downloads)
* Vagrant - 快速,便携式,动态配置的虚拟机工具 ，[Vagrant Home](https://www.vagrantup.com) 点击 'download now link'
* Git - 版本控制 [Downloads](http://git-scm.com/downloads)

## 安装

* 复制版本  `git clone https://github.com/huanghua581/Laravel4-Vagrant.git`
* 在 `Laravel4-Vagrant` 文件夹运行 `vagrant up` 
* （在您第一次运行它需要下载虚拟机镜像，大约300MB。根据你的下载速度这可能需要一些时间！）
* 在第一运行的时候，Vagrant 会根据 puppet 配置文件配置系统，这也需要一些时间。
* 当安装成功时， 打开浏览器浏览 http://localhost:8888 

*注意: 你可能需要更改 www/app/storage 文件夹权限为 777 在你的主机系统上* 

例如: `chmod -R 777 www/app/storage/`

## 使用

一些基本的配置参数

### 端口

* 8888 - Apache
* 8889 - MySQL 
* 5433 - PostgreSQL


### MySQL/PostgreSQL 默认配置

* User: root
* Password: (blank) [空]
* DB Name: database


### PHPmyAdmin

访问：http://localhost:8888/phpmyadmin

### PHP XDebug

XDebug 已经安装，但是 **默认没有开启**， 因为开启影响性能。

开启 XDebug:

1. 启动之前设置参数 `puppet/manifests/phpbase.pp` 添加 `$use_xdebug = "1"` ；
2. 然后启动 `vagrant up` 或者在虚拟机运行的时候执行 `vagrant provision` ；
3. 这样你就可以用 XDebug 调试了 ， **默认端口 9001** 。

**XDebug 工具**

* [SublimeXDebug](https://github.com/Kindari/SublimeXdebug) - 免费, SublimeText 插件
* [MacGDBP](http://www.bluestatic.org/software/macgdbp/) - 免费, Mac OSX
* [Codebug](http://www.codebugapp.com/) - 收费, Mac OSX


_注意: 所有 XDebug 配置信息都可以在 PHP.ini 模板文件修改 `puppet/modules/php/templates/php.ini.erb`_

### Vagrant

Vagrant [在线文档](http://vagrantup.com/v1/docs/index.html)  
一些常用命令 : 

* `vagrant up` 开机和配置虚拟机
* `vagrant suspend` 虚拟机睡眠，可以用 `vagrant resume` 唤醒
* `vagrant halt` 关闭虚拟机
* `vagrant ssh`  进入虚拟机shell环境

----
##### 虚拟机软件列表 #####

* OS     - Ubuntu 12.04
* Apache - 2.2.22
* PHP    - 5.4.17
* MySQL  - 5.5.24
* PostgreSQL - 9.1
* Beanstalkd - 1.4.6
* Redis - 2.2.12
* Memcached - 1.4.13
