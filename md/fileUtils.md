###4文件下载
![](https://github.com/abook23/GodLibrary/blob/master/files/imags/downloadDialog.png)
```java
   String fileName = url.substring(url.lastIndexOf("/") + 1);
   DownloadDialog downloadDialog = DownloadDialog.newInstance(url, "/DownLoad", fileName);
   downloadDialog.show(getFragmentManager(), "DownloadDialog");
```

###5文件上传
####Multipart 方式上传 (表单方式提交)
前台
```java
public String uploadFile(String url,File... files)
public String uploadFile(String url, Map<String, String> mapParams, File... files)
public String uploadFile(String url, Map<String, String> mapParams, Map<String, File> files)
```
```java
//初始化
UploadByMultipart upload = UploadByMultipart.newInstance();
        try {
			//上传文件
            upload.uploadFile("url",new File("path"));
			//上传量监听
            upload.setUploadListener(new UploadListener() {
                @Override
                public void transferred(long num) {
                    //当前上传量
                }

                @Override
                public void contentLength(long length) {
                    //文件大小
                }

                @Override
                public void uploadSuccess(Object data) {
                    //上传完成 服务器返回
                }
            });
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
```

后台
[FileUploadController.java](https://github.com/abook23/GodLibrary/blob/master/files/java/FileUploadController.java "FileUploadController.java")

####httpservlet 方式上传
前台代码
```java
UploadUtils.uploadFile(File file, String RequestURL)
```
后台代码
[UploadServlet.java](https://github.com/abook23/GodLibrary/blob/master/files/java/UploadServlet.java "UploadServlet.java")
