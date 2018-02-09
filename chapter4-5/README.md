**Spring MVC常用注解**
Spring MVC常用以下几个注解：

（1）@Controller

    @Controller注解在类上，表明这个类是Spring MVC里的Controller,将其声明为Spring的一个Bean，Dispatchar Servlet会自动扫描
 注解了此注解的类，并将We请求映射到注解了@RequestMapping的方法上。在声明普通Bean的时候,使用@Component、@Service、@Repository
 和@Controller是等同的,因为@Service、@Repository、@Controller都组合了@Compoment元注解；但在Spring MVC声明控制器Bean的时候
 ，只能使用@Controller。
 
（2）@RequestMapping
    @RequestMapping注解是用来映射Web请求（访问路径和参数）、处理类和方法的。@RequestMapping可注解在类或方法上。注解在方法上
 的@RequestMapping路径会继承注解在类上的路径，@RequestMapping支持Servlet的request和response作为参数，也支持request和response
 的媒体类型进行配置。
 
（3）@ResponseBody
    @ResponseBody支持将返回值放在response体内，而不是返回一个页面。基于Ajax的程序时候，可以以此注解返回数据而不是页面；此
 注解可放置在返回值前或者方法上。
 
（4）@RequestBody
    @RequestBody允许request的参数在request体中，而不是在直接链接在地址后面。此注解放置在参数前。
    
（5）@PathVariable
    @PathVariable用来接收路径参数，如/news/001，可接收001作为参数，注解放置在参数前。
    
（6）@RestController
    @RestController是一个组合注解，组合了@Controller和@ResponseBody，这就意味着当只开发一个和页面交互数据控制的时候，需要
 此注解。若没有此注解，要想实现上述功能，则需要自己在代码中加@Controller和@ResponseBody两个注解。
    
=============================================================================
**静态资源映射**
程序的静态文件（js、css、图片）等需要直接访问这时可以配置重写addResourceHandlers方法来实现。

**`Spring MVC 拦截器配置`**
    拦截器（Interceptor）实现每一个请求处理后进行相关的业务处理，类似于Servlet的Filter。
    
    可以让普通的Bean实现HanlderInterceptor接口或者继承HanlderInterceptorAdapter类来实现自定义拦截器。
    通过重写WebMvcConfigurerAdapter的addInterceptors方法来注册自定义的拦截器。
    
    
**@ControllerAdvice**
    通过@ControllerAdvice，将对于控制器的全局配置放置在同一个位置，注解了@Controller的类的方法可以使用
    @ExceptionHandler、@InitBinder、@ModelAttribute注解到方法上，这对所有注解了@RequestMapping的控制器
    内的方法有效。
    
    @ExceptionHandler:用于全局处理控制器里的异常。
    
    @InitBinder:用来设置WebDataBinder，WebDataBinder用来自动绑定前台请求参数到Model中。
    
    @ModelAttribue:@ModelAttribue本来的作用是绑定键值对到Model里，此处是让全局的@RequestMapping都能获得
    在此设置的键值对。
 
======================================================================================= 
**Spring MVC的高级配置**