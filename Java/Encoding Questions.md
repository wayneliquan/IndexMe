1. 如果使用crontab启动java 进程，由于crontab的shell不知加载/etc/profile的配置文件，所有默认的编码不一定是UTF-8， 需要在启动的时候手动加载一次

   ```source /etc/profile```

2. 

