# mybatis框架二

### 必知必会

> 课程中mybatis 基本配置

- 数据库连接的配置
- 别名的配置
- 方法名和xml映射的相关配置



### 常见问题

- 无法映射 cn.itcast.mybaitis.findAll
  - xml文件的名字和java类dao的名字不同



### 面试题

#### 使用 MyBatis 的 mapper 接口调用时有哪些要求？

```
1. Mapper 接口方法名和 mapper.xml 中定义的每个 sql 的 id 相同
2. Mapper 接口方法的输入参数类型和 mapper.xml 中定义的每个 sql 的 parameterType 的类型相同
3. Mapper 接口方法的输出参数类型和 mapper.xml 中定义的每个 sql 的 resultType 的类型相同
4. Mapper.xml 文件中的 namespace 即是 mapper 接口的类路径

```

#### 当实体类中的属性名和表中的字段名不一样 ，怎么办 ？

- 第1种： 通过在查询的sql语句中**定义字段名的别名，让字段名的别名和实体类的属性名一致**

```mysql
<select id="findAll" resultMap="accountMap">
	select u.*,a.id as aid,a.uid,a.money from account a,user u where a.uid =u.id;
</select>

```

- 第2种： **通过来映射字段名和实体类属性名的一一对应的关系**

```mysql
<!-- 建立对应关系 -->
<resultMap type="account" id="accountMap">
  <id column="aid" property="id"/>
  <result column="uid" property="uid"/>
  <result column="money" property="money"/>
  <!-- 它是用于指定从表方的引用实体属性的 -->
  <association property="user" javaType="user">
    <id column="id" property="id"/>
    <result column="username" property="username"/>
    <result column="sex" property="sex"/>
    <result column="birthday" property="birthday"/>
    <result column="address" property="address"/>
  </association>
</resultMap>
```