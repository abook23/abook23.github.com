#1项目引用 

android studio
```java
compile 'com.abook23:godlibrary:1.0'
```

eclipse
```java
<dependency>
  <groupId>com.abook23</groupId>
  <artifactId>godlibrary</artifactId>
  <version>1.0</version>
  <type>pom</type>
</dependency>
```

aar 引用 记得添加第三方引用
```java
    compile 'com.google.code.gson:gson:2.6.2'//万能的Google json解析
    compile 'com.github.chrisbanes.photoview:library:1.2.4'//图片放大缩小
    compile 'org.apache.httpcomponents:httpclient-android:4.3.5.1'//apache http
    compile 'org.apache.httpcomponents:httpmime:4.5.2'//上传进度需要的包
```
