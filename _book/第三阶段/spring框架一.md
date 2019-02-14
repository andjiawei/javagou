# spring框架一



#### 必知必会

- 知道什么是spring 以及spring 的优势
- 能讲出IOC的概念及作用
- 会配置IOC



#### 面试题

- BeanFactory 和ApplicationContext的区别

```java
BeanFactory和ApplicationContext都是接口，并且ApplicationContext是BeanFactory的子接口。

BeanFactory是Spring中最底层的接口，提供了最简单的容器的功能，只提供了实例化对象和拿对象的功能。而ApplicationContext是Spring的一个更高级的容器，提供了更多的有用的功能。 

ApplicationContext提供的额外的功能：国际化的功能、消息发送、响应机制、统一加载资源的功能、强大的事件机制、对Web应用的支持等等。

加载方式的区别：BeanFactory采用的是延迟加载的形式来注入Bean；ApplicationContext则相反的，它是在Ioc启动时就一次性创建所有的Bean,好处是可以马上发现Spring配置文件中的错误，坏处是造成浪费。
```

- 解释Spring支持的几种bean的作用域

```
Spring框架支持以下五种bean的作用域：

singleton :bean在每个Spring ioc 容器中只有一个实例。

prototype：一个bean的定义可以有多个实例。

request：每次http请求都会创建一个bean，该作用域仅在基于web的Spring ApplicationContext情形下有效。

session：在一个HTTP Session中，一个bean定义对应一个实例。该作用域仅在基于web的Spring ApplicationContext情形下有效。

global-session：在一个全局的HTTP Session中，一个bean定义对应一个实例。该作用域仅在基于web的Spring ApplicationContext情形下有效。

缺省的Spring bean 的作用域是Singleton.
```

- ApplicationContext  接口 的实现类

```
ClassPathXmlApplicationContext ：
它是从类的根路径下加载配置文件 推荐使用这种

FileSystemXmlApplicationContext ：
它是从磁盘路径上加载配置文件，配置文件可以在磁盘的任意位置。

AnnotationConfigApplicationContext:
当我们使用注解配置容器对象时，需要使用此类来创建 spring 容器。它用来读取注解
```

- 实例化 Bean 的三种方式

```
参考 资料中 3.3.2.3节

第一种方式：使用默认无参构造函数
第二种方式：spring  管理静态工厂- 使用静态工厂的方法创建对象
第三种方式：spring  管理实例工厂- 使用实例工厂的方法创建对象
```

