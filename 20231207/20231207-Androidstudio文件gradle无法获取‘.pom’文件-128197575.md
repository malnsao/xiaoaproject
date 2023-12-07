Could not GET
‘<https://dl.google.com/dl/android/maven2/com/android/tools/build/gradle/3.1.3/gradle-3.1.3.pom>
‘. Received status code 400 from server: Bad Request

#### 解决方案：

修改文件 `build.gradle`

**将原来的：**

> buildscript {  
>  repositories {  
>  google()  
>  jcenter()  
>  }  
>  ...  
>  }

**修改成：**

> buildscript {  
>  repositories {  
>  google()  
>  jcenter()  
>  maven {  
>  url 'http://maven.aliyun.com/nexus/content/groups/public/'  
>  }  
>  }  
>  ...  
>  }

