# springmvc框架二

### 必知必会

- 文件上传的流程与代码编写
- 自定义异常的流程



### 常见异常

- 上传文件时xml中的属性 value 和name 写混 导致upload为null



### 面试题

- SpringMVC 常用注解都有哪些？

  ```
  @requestMapping 用于请求 url 映射。
  @RequestBody 注解实现接收 http 请求的 json 数据，将 json 数据转换为 java 对象。
  @ResponseBody 注解实现将 controller 方法返回对象转化为 json 响应给客户。
  ```

- SpringMVC怎么样设定重定向和转发的？

```

（1）在返回值前面加"forward:"就可以让结果转发,譬如"forward:user.do?name=method4"

（2）在返回值前面加"redirect:"就可以让返回值重定向,譬如"redirect:http://www.baidu.com"

```

