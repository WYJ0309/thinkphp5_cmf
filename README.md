1：lamp环境已搭建完成
----参考链接：https://www.cnblogs.com/impy/p/8040684.html
2：下载thinkphp5
3：
---sudo mv thinkphp_5.0.15_full.zip /var/www/
---sudo unzip -n thinkphp_5.0.15_full.zip -d ./html/thinkphp5  不覆盖的解压到当前目录的thinkphp5文件夹下面
4：
--- cd /etc/apache2/sites-available
--- sudo cp 000-default.conf tp5.conf
--- sudo gedit tp5.conf
5:
--- sudo service apache2 restart
--- sudo gedit /etc/hosts




lnmp安裝

按照此文安装完成:http://www.chinaz.com/web/2016/0729/558827.shtml



sudo apt-get install nginx

所有的配置文件都在/etc/nginx下，并且每个虚拟主机已经安排在了/etc/nginx/sites-available下
程序文件在/usr/sbin/nginx
日志放在了/var/log/nginx中
并已经在/etc/init.d/下创建了启动脚本nginx
默认的虚拟主机的目录设置在了/var/www/nginx-default
启动nginx
sudo /etc/init.d/nginx start
查看到歡迎頁面，說明nginx安裝成功

配置支持php的環境
https://blog.csdn.net/cse110/article/details/70226437
sudo service php7.0-fpm reload 或 service php7.0-fpm start

然后就可以访问了，http://localhost/ ， 一切正常！如果不能访问，先不要继续，看看是什么原因，解决之后再继续。

配置網站 www.tp5.my
1：复制default文件为tp5
2：增加index.php到指引文件
3:sudo ln -s /etc/nginx/sites-available/tp5 /etc/nginx/sites-enabled创建软连接到站点激活目录，重启nginx
每修改完配置信息后操作下条命令
sudo systemctl restart php7.0-fpm nginx 


安装thinkphp5
首先修改/var/www的目录权限和所属组
修改权限为由733改为755  sudo chmod g+w www
修改www目录的所属组及用户拥有者  chown www-data:www-data -R www

安装tp5
