No validator could be found for constraint 'javax.validation.constraints.NotBlank' validating type 'java.lang.String'

- 原因
```
@NotBlank is new in Bean Validation 2.0 so I suspect you have an old Hibernate Validator version (e.g. 5.x) in your classpath somehow.  
```

- 解决  
<pre><code>
查看哪里引用了hibernate-validator　mvn dependency:tree　
使用最新版本的hibernate-validator
</code></pre>  
-  引用资料
[no-validator-could-be-found-for-constraint-javax-validation-constraints-notblan](https://stackoverflow.com/questions/52878299/no-validator-could-be-found-for-constraint-javax-validation-constraints-notblan)

