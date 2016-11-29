作者：彭松
链接：https://zhuanlan.zhihu.com/p/21353217
来源：知乎
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

RedirectAttributes 是Spring mvc 3.1版本之后出来的一个功能，专门用于重定向之后还能带参数跳转的的工具类
他有两种带参的方式：

第一种：

```
redirectAttributes.addAttributie("prama",value); 这种方法相当于在重定向链接地址追加传递的参数，例如:

redirectAttributes.addAttributie("prama1",value1);

redirectAttributes.addAttributie("prama2",value2);

return:"redirect：/path/list"
```

以上重定向的方法等同于 return:"redirect：/path/list？prama1=value1&prama2=value2 " ，注意这种方法直接将传递的参数暴露在链接地址上，非常的不安全，慎用。

第二种：

```
redirectAttributes.addFlashAttributie("prama",value); 这种方法是隐藏了参数，链接地址上不直接暴露，但是能且只能在重定向的 “页面” 获取prama参数值。其原理就是放到session中，session在跳到页面后马上移除对象。如果是重定向一个controller中是获取不到该prama属性值的。除非在controller中用(@RequestPrama(value = "prama")String prama)注解，采用传参的方式。页面获值例如：

redirectAttributes.addFlashAttributie("prama1",value1);

redirectAttributes.addFlashAttributie("prama2",value2);

return:"redirect：/path/list.jsp"
```

在以上参数均可在list.jsp页面使用EL表达式获取到参数值${prama*}

controller获得redirectAttributes重定向的值例如：

```
redirectAttributes.addFlashAttributie("prama1",value1);

redirectAttributes.addFlashAttributie("prama2",value2);

return:"redirect：/path/list/"

@RequestMapping("list")
public List<Student> list(@RequestPrama(value = "prama1")String  prama1,
   @RequestPrama(value = "prama2")String  prama2,...
){
    //TODO
    //your code

}
```
通过在controller中的list方法体中可以获取到参数值。

---

```
public String save(@ModelAttribute("group") Group group, RedirectAttributes redirectAttributes) {
	accountManager.saveGroup(group);
	redirectAttributes.addFlashAttribute("message", "修改权限组成功");
	return "redirect:/account/group/";
}
```