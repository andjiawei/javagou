# mybatis框架三



### 必知必会

- 了解延迟加载的逻辑
- 了解一级缓存 二级缓存



#### 面试题

##### 接口绑定有几种实现方式,分别是怎么实现的?

```
接口绑定有两种实现方式：
- 一种是通过注解绑定,就是在接口的方法上面加上@Select@Update等注解里面包含Sql语句来绑定
- 另外一种就是通过xml里面写SQL来绑定,在这种情况下,要指定xml映射文件里面的namespace必须为接口的全路径名.

```

##### Mybatis的Xml映射文件中，不同的Xml映射文件，id是否可以重复？

```
如果配置了namespace那么当然是可以重复的，因为我们的Statement实际上就是namespace+id

如果没有配置namespace的话，那么相同的id就会导致覆盖了。

```

##### 通常一个Xml映射文件，都会写一个Dao接口与之对应，请问，这个Dao接口的工作原理是什么？Dao接口里的方法，参数不同时，方法能重载吗？

```
- Dao接口，就是人们常说的Mapper接口，接口的全限名，就是映射文件中的namespace的值，接口的方法名，就是映射文件中MappedStatement的id值，接口方法内的参数，就是传递给sql的参数。
- Mapper接口是没有实现类的，当调用接口方法时，接口全限名+方法名拼接字符串作为key值，可唯一定位一个MappedStatement

举例：
    com.mybatis3.mappers.StudentDao.findStudentById，
    可以唯一找到namespace为com.mybatis3.mappers.StudentDao下面id = findStudentById的MappedStatement。在Mybatis中，每一个<select>、<insert>、<update>、<delete>标签，都会被解析为一个MappedStatement对象。
    
Dao接口里的方法，是不能重载的，因为是全限名+方法名的保存和寻找策略。

Dao接口的工作原理是JDK动态代理，Mybatis运行时会使用JDK动态代理为Dao接口生成代理proxy对象，代理对象proxy会拦截接口方法，转而执行MappedStatement所代表的sql，然后将sql执行结果返回

```

#### 试讲下mybatis 的一级 二级缓存

```
- 数据的查询执行的流程就是 二级缓存 -> 一级缓存 -> 数据库
- 一级缓存是 SqlSession 级别的缓存，只要 SqlSession 没有 flush 或 close，它就存在。
- 当调用 SqlSession 的修改，添加，删除，commit()，close()等 方法时，就会清空一级缓存
- 缓存的实质就是保存在PerpetualCache 类中的 Hashmap，key为hashCode+sqlId+Sql语句。value为从查询出来映射生成的java对象
-二级缓存是 mapper 映射级别的缓存，多个 SqlSession 去操作同一个 Mapper 映射的 sql 语句，多个
- SqlSession 可以共用二级缓存，二级缓存是跨 SqlSession 的。
-在分布式环境下，由于默认的Mybatis Cache实现都是基于本地的，分布式环境下必然会出现读取到脏数据，需要使用集中式缓存将Mybatis的Cache接口实现，有一定的开发成本，不如直接用Redis，Memcache实现业务上的缓存就好了
```

