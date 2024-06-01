### [依赖注入(Dependency Injection)](#)
> **介绍**：是一种软件设计模式，也是实现控制反转的其中一种技术。這种模式能让一个物件接收它所依赖的其他物件。**依赖** 是指接收方所需的对象。**注入** 是指将 **依赖** 传递给接收方的过程。
**此模式确保了任何想要使用给定服务的物件不需要知道如何建立這些服务**。
----

### [1. 基本概念](#)
**依赖注入** 这种技术手段实现功能模块对其依赖组件的**控制反转**,将 **依赖组件** 的配置和使用分离开。

**组件和服务:** 
* 组件是一种独立的、可重用的软件模块，它封装了某一特定功能或一组相关功能。
* 服务是一种独立的功能单元，它通过网络或其他通信机制向其他系统或组件提供特定的功能。

> 服务的一个常见实现形式是微服务架构，在这种架构中，应用被拆分为多个小的、独立部署的服务，每个服务实现特定的业务功能。

组件和服务的区别
* 组件通常是在同一个应用内部运行的（如 jar 文件、dll 或者源码导入），而服务通常是在不同的网络节点上独立部署和运行的（如 WebService、消息系统、RPC 或者 Socket）。
* 组件之间的通信通常是通过函数调用或消息传递，而服务之间的通信则通常是通过网络请求（如HTTP）进行的。
* 服务的独立性更强，可以独立部署和扩展，而组件通常依赖于宿主应用的运行环境。

依赖注入的形式主要有三种，分别将它们叫做
* 构造注入（ Constructor Injection）
* 属性注入（ Setter Injection）
* 方法注入（ Interface Injection）

```cpp
class UserController{
private:
    MysqlConnectionService service; //数据库服务

    UserController(){
        service = MysqlConnectionService("127.0.0.1",3306, "root", "123456", "test");
    }
};
// 使用构造注入
class UserController{
private:
    MysqlConnectionService service; //数据库服务

    UserController(MysqlConnectionService _service){
        service = _service;
    }
};
```

#### 1.1 控制反转简析
控制反转IoC(Inversion of Control)是说创建对象的控制权进行转移 **(获得依赖对象的方式反转了)** ，以前创建对象的主动权和创建时机是由自己把控的，而现在这种权力转移到第三方，比如转移交给了IoC容器，它就是一个专门用来创建对象的工厂...。

> 控制反转（创建对象实例的控制权反转），说的是一个类A要调用另一个类B，本来应该在类A里面创建B的实例的，控制权在A手里。现在用了Spring了，有了IOC，控制权就不在A手里了，而是交到Spring的IOC容器了，A要用到B，那Spring就把B分给A了。

IoC的一个重点是在系统运行中，动态的向某个对象提供它所需要的其他对象。这一点是通过DI（Dependency Injection，依赖注入）来实现的。


### 参考资料
* [Spring实现IOC（控制反转）的三种方式 CSDN](https://blog.csdn.net/zhaoraolin/article/details/78941062)
* [深入浅出依赖注入](https://segmentfault.com/a/1190000014803412)
