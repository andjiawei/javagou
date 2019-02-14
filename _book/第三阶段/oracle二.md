# oracle二

### 一定要会

- 课程中所有的SQL语句




### 面试题

-  Oracle中function和procedure的区别？ 

```
1). 可以理解函数是存储过程的一种 
2). 函数可以没有参数,但是一定需要一个返回值，存储过程可以没有参数,不需要返回值 
3). 函数return返回值没有返回参数模式，存储过程通过out参数返回值, 如果需要返回多个参数则建议使用存储过程 
4). 在sql数据操纵语句中只能调用函数而不能调用存储过程
```

- 说说oracle中的经常使用到的函数 

```

Length 长度、 lower 小写、upper 大写， to_date 转化日期， to_char转化字符 
Ltrim 去左边空格、 rtrim去右边空格，substr取字串，add_month增加或者减掉月份、to_number转变为数字 
```

- Oracle 中是如何进行分页查询的？

```sql
Oracle 中使用 rownum 来进行分页
select * from
( select rownum r,a from tabName where rownum <= 20 )
where r > 10
```

