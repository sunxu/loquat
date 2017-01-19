#背景介绍
PHP可以用来做HTTP服务，也可以做异步服务（也就是通常说的脚本，比如消费队列中的数据、定时扫mysql统计数据、增量同步mysql中的数据到redis等），而当前主流PHP框架均只适合做HTTP服务，不适合做异步服务，虽然大多数框架稍微修改就可以支持异步服务，但是有不少功能无法实现，如：服务的自动化部署和卸载、服务的监控和启动、服务的分布式执行等。Loquat就是这样一种专门做异步服务的PHP框架。
#文件介绍
###script.php 
相当于HTTP服务框架中的index.php，用户可以在此文件中加入自动加载业务框架的代码。
###exec.sh
批量启动服务的脚本，比如exec.sh /usr/local/php7/bin/php php7.ini script.php PerSecond#批量启动每秒启动一次的服务。
###php7.ini
服务启动时的配置文件，php会用-c参数把其加载进来。
###install7.ini
服务安装时的配置文件，需要配置上php，php.ini，以及服务的入口文件script.php。
###install.sh
服务安装脚本，会把服务安装到crontab中。
