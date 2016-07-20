##等待弹框
```java
    public void onClick0() {
        DialogLoading dialogLoading = new DialogLoading(context);
        dialogLoading.show("显示的消息");
        //dialogLoading.msg.setText("改变消息内容");
        //dialogLoading.dismiss();//关闭弹框
    }
```

##时间选择
```java
    public void onClick1() {
        final DialogDate dialogDate = new DialogDate();
        dialogDate.show(context);
        dialogDate.but_ok.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                DatePicker datePicker = dialogDate.datePicker;
                //DatePicker 操作了
            }
        });
    }
```

##消息弹框
```java
    public void onClick3() {
        DialogMsgBox dialogMsgBox = new DialogMsgBox(context);
        dialogMsgBox.show("标题", "内容");
        //确定
        dialogMsgBox.but_ok.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {

            }
        });
    }
```


##下载弹框
```xml
	在AndroidManifest.xml 添加 service
	<service android:name=".service.DownloadService"/>
```
```java
    public void onClick4() {

        String url = "htttp://xxx/xxx.apk";
        String fileName = url.substring(url.lastIndexOf("/") + 1);
        DownloadDialog downloadDialog = DownloadDialog.newInstance(url, "/DownLoad", fileName);
        downloadDialog.show(getFragmentManager(), "DownloadDialog");
    };
```

##listView 弹框
```java
    public void onClick5() {
        DialogListView dialogListView = new DialogListView();
        dialogListView.show(context);
        dialogListView.listView;//listview 操作
        //dialogListView.dismiss();//关闭
    }
```

