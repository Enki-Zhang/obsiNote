
## Lombok使用


使用@**`RequiredArgsConstructor`** 进行构造器注入 仅对 `final` 字段生成构造器，强制依赖不可变，更安全。
 生成的构造器按照字段顺序进行

相比于使用Autowired注解 能够减少对反射的依赖，同时方便测试

## N+1查询问题

N+1 查询问题（N+1 Query Problem）是指在数据库查询中，因不合理的查询设计或数据访问模式，导致大量冗余查询执行，从而严重影响性能的现象。


案例：
1： 查询一次订单主表
N   根据每次主表的信息循环查询主表对应的明细
那么总的查询次数是 一次主表+ N次明细



## MapStruct



## lombok

@SneakyThrows 可以对一些受检异常进行非显示的关心

## docker常用命令

-v 将本地目录挂载到容器目录中

语法： -v 本地目录:容器目录


## 流式查询

查询的数据会放在内存中进行比较 对于大量数据而言会


## 端口查询

查询端口 命令 得到对应的进程
netstat -ano | findstr :8080

杀死对应的进程
taskkill /PID 1234 /F


## 事务注解添加的位置
@Transactional 应该尽量放在最小必要的方法上，以避免不必要的性能开销（如锁住过多的资源）。

## 循环依赖

在存在循环依赖的情况下 有可能是将 @Autowired 替换为 @RequiredArgsConstructor（来自 Lombok）完全有可能导致循环依赖问题，从而导致 Spring 启动失败

### 原因分析

  

#### 1. @Autowired vs @RequiredArgsConstructor

  

- **@Autowired**：  
    - 默认用于字段注入或 setter 注入。
      
    - Spring 在创建 Bean 后，通过反射注入依赖，支持延迟加载。
      
    - 对于循环依赖，Spring 可以通过代理和延迟注入打破循环（默认情况下允许循环依赖）。
      
    
  
- **@RequiredArgsConstructor**：  
    - Lombok 注解，会为所有标有 @NonNull 或 final 的字段生成构造器。
      
    - 等价于构造器注入（Constructor Injection）。
      
    - Spring 在创建 Bean 时，必须先解析所有构造器参数（即依赖的 Bean），这会导致依赖注入发生在 Bean 初始化之前。