# LitePalTest

导入依赖时出错：

```
android studio引入 implementation 'org.litepal.guolindev:core:3.2.3'出错，
报错信息：

What went wrong:
Execution failed for task ':app:checkDebugAarMetadata'.
Could not resolve all files for configuration ':app:debugRuntimeClasspath'.
Could not find org.litepal.guolindev:core:3.2.3.
Searched in the following locations:

as版本：Android Studio Giraffe | 2022.3.1 Patch 3
用的gradle脚本
是什么原因啊？
```

解决方法：

```
在gradle脚本的setting.gradle文件的dependencyResolutionManagement>repositories选项内添加：

jcenter()
maven { url 'https://jitpack.io' }

sync一下就好了
参考链接：https://www.yii666.com/blog/330831.html
```

这样就可以正常使用依赖了。

第一行代码书籍中的代码有些过时，具体参考：

```
https://github.com/guolindev/LitePal
```

其中更换的有：

```
public class Book extends LitePalSupport 
```

```
LitePal.getDatabase();
```

```
                LitePal.deleteAll(Book.class,"price < ?","15");
```

```
  List<Book> books1 = LitePal.select("name","author","pages")
                        .where("pages > ?","400")
                        .order("pages")
                        .limit(4)
                        .offset(1)
                        .find(Book.class);
```

