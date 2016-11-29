- 修改tinyint长度
tinyint 长度为1，指的是占用1个字节空间，TINYINT(1)、BOOL、BOOLEAN 所占用的存储空间和 TINYINT 一样，都是一个字节；
TINYINT(1) 只是在显示的时候作为一个位进行输出而已，所以设置成TINYINT(4)就可以了

- jdbc连接上加参数
在jdbcUrl添加参数：tinyInt1isBit=false（默认为true）
