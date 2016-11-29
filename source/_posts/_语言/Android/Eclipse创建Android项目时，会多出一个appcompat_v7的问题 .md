# Eclipse创建Android项目时，会多出一个appcompat_v7的问题 

---
### 问题描述：
使用eclipse创建一个Android项目时，发现project列表中会多创建出一个appcompat_v7项目，再创建一个Android项目时，又会再多出一个appcompat_v7_2，如果再次创建，会以此类推地创建出appcompat_v7_x格式的“多余项目”出来（此情况在ADT升级为22.6.x版本后出现，22.3.x前的版本不会有）

-
### 查明原因：
ADT在22.3.x版本前没有出现该情况，升级为22.6.x版本后，才出现该情况，可以猜测是新版本导致。猜测到原因后可以分析下appcompat_v7是用来做什么的，展开appcompat_v7项目，会发现有一个readme.txt文件，双击查看，该文件描述如下：
Library Project including compatibility ActionBar.

This can be used by an Android project to provide
access to ActionBar on applications running on API 7+.

There is technically no source, but the src folder is necessary
to ensure that the build system works.  The content is actually
located in libs/android-support-v7-appcompat.jar.
The accompanying resources must also be included in the application.

字面意思大概可以看出，该项目是一个Library Project， 作用是让你的Android Project 在API 7+的sdk版本（即Android2.1版本）可以访问ActionBar的API，ActionBar相当于用户界面的操作栏，具体ActionBar的解释可以参考：http://developer.android.com/guide/topics/ui/actionbar.html。所以从中可以看出多出这个project是为了兼容低版本的sdk，那我们创建的Android项目是如何引用这个类库项目呢？通过右键点击Android项目---->Properties-->Android，可以查看到该类库项目已被引用进来了。

-
### 解决方法：
appcompat_v7包是一个能让2.1以上全使用上4.0版本的界面的支持库，建项目时选择最低 API 版本大于4.0。