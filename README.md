## Springboot（一）@import导入组件
@Component 代表一个组件

@Controller   代表是一个控制器

@Import({User.class})
//导入组件User类型的组件
复制代码
@Import({User.class, DBAppender.class})
//导入组件User类型的组件,自动创建对应的无参构造器,创建出指定类型的对象
@Configuration(proxyBeanMethods = true)   //告诉Spring boot这是一个配置类 ~~~ 配置文件
public class Myconfig {//@Bean("ABC")
    @Bean
    public User user01() {
        return new User("tom",18);
    }
}
复制代码
这里通过@Import导入了2个组件，同时下面也声明了一个bean组件，因此这里在主程序通过打印可以得到：三个组件

复制代码
 //从容器中获取组件@import
        String[] beanNamesForType = run.getBeanNamesForType(User.class);
        System.out.println("++++++++++++++++++++++++++++++");
        for (String s : beanNamesForType) {
            System.out.println(s);
        }
　　　　//这里会输出2个组件，一个是import注解导入，另一个是bean注解导入

        DBAppender bean1 = run.getBean(DBAppender.class);
        System.out.println(bean1);
复制代码
