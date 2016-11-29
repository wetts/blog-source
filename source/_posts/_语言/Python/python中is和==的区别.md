# python 中 is 和 == 的区别
在 python 中，is 检查两个对象是否是同一个对象,而 == 检查他们是否相等。
Python 中的对象包含三要素：id、type、value。
其中 id 用来唯一标识一个对象，type 标识对象的类型，value 是对象的值。
is 判断的是 a 对象是否就是 b 对象，是通过 id 来判断的。
== 判断的是 a 对象的值是否和 b 对象的值相等，是通过 value 来判断的。
