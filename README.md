## springboot项目启动后执行一段代码的两种方式

- ApplicationRunner
- CommandLineRunner

## ApplicationRunner

```
package com.rumenz;


import org.springframework.boot.ApplicationArguments;
import org.springframework.boot.ApplicationRunner;
import org.springframework.core.annotation.Order;
import org.springframework.stereotype.Component;

@Component
@Order(2)
public class ApplicationRunnerDemo implements ApplicationRunner {


    @Override
    public void run(ApplicationArguments args) throws Exception {

        System.out.println("ApplicationRunner 执行");
    }
}

```

## CommandLineRunner

```
package com.rumenz;


import org.springframework.boot.CommandLineRunner;
import org.springframework.core.annotation.Order;
import org.springframework.stereotype.Component;

@Component
@Order(1)
public class CommandLineRunnerDemo  implements CommandLineRunner {
    @Override
    public void run(String... args) throws Exception {
        System.out.println("CommandLineRunnerDemo 执行了");
    }
}

```

>> 如果同时使用了ApplicationRunner,CommandLineRunner.可以使用@Order(数字)指定执行的顺序,数字越小越先执行


```
//执行结果

2020-06-10 23:17:43.386  INFO 56716 --- [  restartedMain] com.rumenz.DemoApplication               : Started DemoApplication in 15.972 seconds (JVM running for 16.542)
CommandLineRunnerDemo 执行了
ApplicationRunner 执行
```
