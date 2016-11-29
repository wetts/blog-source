### step1：默认会放在~/.m2/repository目录下 （“~”代表用户的目录，比如windows下一般都是C:\Documents and Settings\[你的用户名]\。由于“Documents and Settings”中含有“空格”会导致“Illegal character in path”异常）

安装Maven后我们会在用户目录下发现.m2 文件夹。默认情况下，该文件夹下放置了Maven本地仓库.m2/repository。所有的Maven构件(artifact)都被存储到该仓库中，以方便重用。

### step2：修改配置文件，位置为%MAVEN_HOME%/conf/setting.xml,
```
<!-- localRepository
   | The path to the local repository maven will use to store artifacts.
   |
   | Default: ~/.m2/repository
<localRepository>/path/to/local/repo</localRepository>
-->
```
修改为：
```
<localRepository>D:\Eclipse\jars\maven</localRepository>
```

### step3：修改MyEclipse的MAVEN的存储位置：

进入MyEclipse→window→Preferences→Maven4MyEclipse→Maven→Installations→User Sittings

点击右侧Browse指向%MAVEN_HOME%\conf\settings.xml

----------------------------------------------------------------------

%MAVEN_HOME%代表你的MAVEN所在目录
