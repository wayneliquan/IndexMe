jdbc 访问数据库的流程：

1. 加载驱动

2. 创建链接

3. 执行sql

4. 关闭连接

   ```
   Connection connection = DriverManager.getConnection(url, username, password);
   Statement statement = connection.createStatement();
   statement.execute("sql");
   connection.close();
   ```

1. 如果多个线程同是访问一个Connection有什么问题？

   ```
   对于查询是线性的。
   对于事务是不安全的,如果autocommit为ture, 有可能被其他线程commit;
   ```

2.  如果多个线程同是访问Statement, 并对结果集操作有什么问题？

```
不安全的，有可能不同的线程活的同一个resultSet。
```

