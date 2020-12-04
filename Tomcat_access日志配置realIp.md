Tomcat配置access日志配置realIp



在server.xml添加%{X-Real-IP}i

```xml
<Valve className="org.apache.catalina.valves.AccessLogValve" directory="logs"
               prefix="localhost_access_log" suffix=".txt"
               pattern="%h %l %u %t %{X-Real-IP}i &quot;%r&quot; %s %b" />
```



查看/docs/config/valve.html的配置文件。