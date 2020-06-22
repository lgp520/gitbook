# supervisor总结

supervisor是用于进程管理的一个命令行工具，可以将一个进程设置为守护进程。例如比较简单的做法是：nohup+&。supervisor其实包含两部分，是C/S架构，其本质是一个进程，将所管理的进程作为自己的子进程，且子进程退出时可以自动重启。

## 安装

```shell
apt install supervisor
#pip install supervisor
#brew install supervisor
```

## 启动supervisord

```
supervisord -c /usr/local/etc/supervisord.ini
```

## 启动supervisoctl

supervisorctl默认是通过http与supervisord通信的，在命令行执行supervisorctl即可。

注意：通过http连接时，需要开启supervisord的http配置。

## 配置文件

ubuntu下：

主配置文件在/usr/local/etc/supervisord.ini；

在配置文件里定义管理的进程以及管理的策略，此处不做赘述。

## 几个管理的命令

restart：重启进程，并不会重新读取配置文件，所以服务实际未使用新配置

reread：只会更新配置文件，不会重启进程，所以服务实际未使用新配置

update：更新配置文件，并重启配置文件有更新的进程，相当于 reread + restart，所以服务会使用新配置

reload：重启supervisord，相当于更新所有服务的配置文件，并重启所有服务（**谨慎使用**）