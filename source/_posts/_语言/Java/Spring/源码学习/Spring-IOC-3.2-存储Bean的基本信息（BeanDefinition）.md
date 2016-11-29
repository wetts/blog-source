Spring启动时，读取bean，将每个bean转化为BeanDefinition对象。BeanDefinition保存了一个bean的所有基本信息。

以下是一个BeanDefinition的主要属性：
```
public abstract class AbstractBeanDefinition extends BeanMetadataAttributeAccessor implements BeanDefinition, Cloneable {
    private volatile Object beanClass; // 保存bean的class属性
    private String scope = SCOPE_DEFAULT; // bean是否单例
    private boolean abstractFlag = false; // 保存该bean是否抽象
    private boolean lazyInit = false; // 保存是否延迟初始化
    private int autowireMode = AUTOWIRE_NO; // 保存是否自动装配
    private int dependencyCheck = DEPENDENCY_CHECK_NONE; // 保存是否坚持依赖
    private String[] dependsOn; // 保存该bean依赖于哪些bean
    private boolean autowireCandidate;
    private boolean primary;
    private final Map<String, AutowireCandidateQualifier> qualifiers;
    private boolean nonPublicAccessAllowed;
    private boolean lenientConstructorResolution;
    private ConstructorArgumentValues constructorArgumentValues; // 保存通过构造函数注入的依赖
    private MutablePropertyValues propertyValues; // 保存通过setter方法注入的依赖
    private MethodOverrides methodOverrides;
    private String factoryBeanName;
    private String factoryMethodName;
    private String initMethodName; // 对应init-method属性
    private String destroyMethodName; // 对应destory-method属性
    private boolean enforceInitMethod;
    private boolean enforceDestroyMethod;
    private boolean synthetic;
    private int role;
    private String description;
    private Resource resource;

    ...
}
```
