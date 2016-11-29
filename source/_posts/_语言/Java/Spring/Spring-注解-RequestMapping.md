简介：
@RequestMapping
RequestMapping是一个用来处理请求地址映射的注解，可用于类或方法上。用于类上，表示类中的所有响应请求的方法都是以该地址作为父路径。
RequestMapping注解有六个属性，下面我们把她分成三类进行说明。

1. value， method；
value：     指定请求的实际地址，指定的地址可以是URI Template 模式（后面将会说明）；
method：  指定请求的method类型， GET、POST、PUT、DELETE等；

2. consumes，produces；
consumes： 指定处理请求的提交内容类型（Content-Type），例如application/json, text/html;
produces： 指定返回的内容类型，仅当request请求头中的(Accept)类型中包含该指定类型才返回；

3. params，headers；
params： 指定request中必须包含某些参数值是，才让该方法处理。
headers： 指定request中必须包含某些指定的header值，才能让该方法处理请求。