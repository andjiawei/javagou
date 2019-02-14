# mybatis框架一

### 常见错误

- 包名写错 找不到配置文件
- 包含多個findAll 方法,因为注解和xml的方式同时在使用

### 讲道理

- 能讲出每个配置文件的含义，以及如何加载



## 面试题

#### Mybatis 中#和$的区别？

> 详细讲解参考今天笔记2.5.3    2.5.4    2.5.5

```
#{} 表示一个占位符号
通过#{}可以实现 preparedStatement 向占位符中设置值，自动进行 java 类型和 jdbc 类型转换，
#{}可以有效防止 sql 注入。 #{}可以接收简单类型值或 pojo 属性值。 如果 parameterType 传输单个简单类
型值，#{}括号中可以是 value 或其它名称。
${} 表示拼接 sql  串
通过${}可以将 parameterType 传入的内容拼接在 sql中且不进行 jdbc 类型转换， ${}可以接收简
单类型值或 pojo 属性值，如果 parameterType 传输单个简单类型值，${}括号中只能是 value。
一般能用#的就别用$.
```

#### Mybatis 的编程步骤是什么样的？

```
1、创建 SqlSessionFactory
2、通过 SqlSessionFactory 创建 SqlSession
3、通过 sqlsession 执行数据库操作
4、调用 session.commit()提交事务
5、调用 session.close()关闭会话
```



#### JDBC 编程有哪些不足之处，MyBatis 是如何解决这些问题的？

```
1. 数据库链接创建、释放频繁造成系统资源浪费从而影响系统性能，如果使用数据库链接池可解决此问题。
解决：在 SqlMapConfig.xml 中配置数据链接池，使用连接池管理数据库链接。
2. Sql 语句写在代码中造成代码不易维护，实际应用 sql 变化的可能较大，sql 变动需要改变 java 代码。
解决：将 Sql 语句配置在 XXXXmapper.xml 文件中与 java 代码分离。
3. 向 sql 语句传参数麻烦，因为 sql 语句的 where 条件不一定，可能多也可能少，占位符需要和参数一一对应。
解决： Mybatis 自动将 java 对象映射至 sql 语句。
4. 对结果集解析麻烦，sql 变化导致解析代码变化，且解析前需要遍历，如果能将数据库记录封装成 pojo 对象解
析比较方便
解决：Mybatis 自动将 sql 执行结果映射至 java 对象。
```

