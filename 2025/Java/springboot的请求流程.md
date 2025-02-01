
![file-20250107093220866.png](https://raw.githubusercontent.com/Enki-Zhang/blog_img/master/20250107093220.png)

执行顺序：

客户端请求 -> 过滤器(Filter) -> DispatcherServlet -> 拦截器(Interceptor preHandle) -> Controller -> 返回值处理 -> 拦截器(Interceptor postHandle) -> 拦截器(Interceptor afterCompletion) -> 过滤器(Filter doFilter) -> 响应客户端

- 拦截器

Interceptor 是 Spring MVC 提供的一种机制，用于在请求处理的不同阶段（如请求到达控制器之前、控制器方法执行之后、视图渲染之前等）插入自定义逻辑。拦截器的主要作用是对请求进行预处理或后处理，例如权限校验、日志记录、性能监控等。
在自定义逻辑中，拦截器主要定义方法为：
1. preHandle： 在请求到达 controller 方法之前执行，用于日志记录，参数校验，权限校验等；返回 false 请求将中断，不会继续执行以后的逻辑；
2. postHandle：在控制器方法执行之后、视图渲染之前执行。通常用于修改模型数据或视图；
3. afterCompletion：在请求完成之后执行（视图渲染之后）。通常用于资源清理、日志记录等。
自定义的拦截器需要实现 HandlerInterceptor 方法 那么这里的 handler 的类型通常是 HandlerMethod，它封装了控制器方法的相关信息。通过 handler 可以获取控制器方法、方法注解、方法参数等信息



## 过滤器和拦截器区别

**拦截器（Interceptor）** 模式有一个局限性：它只能在 **Controller 层** 进行拦截和校验，而无法在 **Service 层** 或 **DAO 层** 等其他代码中使用。这是因为拦截器是基于 **Spring MVC 框架** 的，它的设计初衷是为了拦截 HTTP 请求，并在请求到达 Controller 之前或之后执行一些逻辑。
关于过滤器

但是过滤器也有一些缺点，比如：

1. 由于太过底层，导致无法率先拿到`HandlerMethod`对象，无法据此添加一些额外功能。
2. 由于拦截的太全面了，导致我们需要对很多特殊路由(如`/favicon.ico`)做一些额外处理。
3. 在Spring中，过滤器中抛出的异常无法进入全局`@ExceptionHandler`，我们必须额外编写代码进行异常处理。

- @Order order注解的作用
  用于控制Bean的加载顺序 AOP切面的执行顺序