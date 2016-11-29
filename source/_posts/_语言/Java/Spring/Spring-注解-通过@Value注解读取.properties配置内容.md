```
@Controller
@RequestMapping("/value")
public class ValuePropertyController extends ApplicationController{

    @Value("#{configProperties['jdbc.jdbcUrl']}")
    private String jdbcUrl;

    @RequestMapping
    public String value(){
        System.out.println(jdbcUrl);
        return "";
    }
}
```

---

applicationContext.xml
```
<bean id="configProperties" class="org.springframework.beans.factory.config.PropertiesFactoryBean">
   <property name="locations">
       <list>
           <value>classpath:database.properties</value>
       </list>
   </property>
</bean>
<bean id="propertyConfigurer" class="org.springframework.beans.factory.config.PreferencesPlaceholderConfigurer">
    <property name="properties" ref="configProperties" />
</bean>
```

---

database.properties
```
jdbc.jdbcUrl=jdbc:mysql://localhost:3306/commentDemo?useUnicode=true&characterEncoding=UTF-8
```