---
title: 如何优雅地使用 spock 框架写单测
date: 2024-07-26T22:01:31+08:00
draft: true
author: JackyLee
tags: [单元测试, spock, java, groovy]
categories: [groovy, 测试]
comment: true
---

## 依赖

```xml
<!-- 1.Spock 相关 -->
<dependency>
    <groupId>org.spockframework</groupId>
    <artifactId>spock-core</artifactId>
    <version>1.3-groovy-2.4</version>
    <scope>test</scope>
</dependency>
<dependency>
    <groupId>org.spockframework</groupId>
    <artifactId>spock-spring</artifactId>
    <version>1.3-groovy-2.4</version>
    <scope>test</scope>
</dependency>
<!-- 2.PowerMock 相关-->
<dependency>
    <groupId>org.powermock</groupId>
    <artifactId>powermock-module-junit4</artifactId>
    <version>2.0.4</version>
    <scope>test</scope>
</dependency>
<dependency>
    <groupId>org.powermock</groupId>
    <artifactId>powermock-api-mockito2</artifactId>
    <version>2.0.4</version>
    <scope>test</scope>
</dependency>
```

## 单测 Demo

### 静态类单测 Demo

```groovy
@RunWith(PowerMockRunner.class)
@PowerMockRunnerDelegate(Sputnik.class) // 交给 spock 代理执行
@PrepareForTest([静态类.class])
@SuppressStaticInitializationFor(["静态类全名"]) // 限制静态类里的静态代码块初始化
class StaticMethodSpec extends Specification {

    def service = Mock(UserService)

    def controller = new UserController(userService: service)

    void setup() {
        // Mock静态类
        PowerMockito.mockStatic(静态类.class)
    }

    @Unroll
    def "测试类名 #desc"() {
        given: "给定条件"
        def user = service.getById(_ as Integer) >> [new User(name: "Alice", age: 12), null]
        def map = [k1:v1, k2:v2]
        def list = [1,2,3]

        and: "mock静态方法返回值"
        PowerMockito.when(静态类.静态方法(Mockito.any())).thenReturn(自己想要的返回值)

        when: "调用时"
        def res = controller.getById(v_id)


        then: "比较"
        res != exp
        // 或者 
        with(res){
            name == v_name
            age == v_age
        }

        where "数据格式"
        desc      | v_id || exp
        "success" | 1    || new User(name: "Alice", age:12)
        "fail"    | -1   || null
    }
}
```

### 捕获异常

```groovy
def "测试类"(){
    //...

    then:
    def exception = thrown(v_expectException)
    exception.code == v_expectCode
    exception.message == v_expectMessage

    // ...
}
```

### 校验参数

```groovy
def "测试类"(){
    //...

    then:
    1 * 某类.某方法({
        it.某属性1 == 属性1
        it.某属性2 == 属性2
    })

    // ...
}
```

## 参考文献

[Spock 单元测试框架介绍以及在美团优选的实践](https://tech.meituan.com/2021/08/06/spock-practice-in-meituan.html)
