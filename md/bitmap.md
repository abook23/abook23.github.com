#图片加载

软缓存+硬缓存 图片缓存地址 跟目录/data2/[package]/。。。。
```java
String uri = "https://www.baidu.com/img/bd_logo1.png";//自动区分网络图片和本地图片
ImageLoader imageLoader = ImageLoader.build(this);

imageLoader.bindBitmap(uri, imageView, false, true);//图片地址，imagView,圆角，缩放
imageLoader.bindBitmap(uri,imageView,150,150,false);//图片地址，imagView,宽，高，圆角
imageLoader.bindBitmap(uri,imageView,150,150,false,true);//图片地址，imagView,宽，高，圆角，缩放


bindBitmap(String uri, ImageView imageView, int width, int height, boolean isRound)
bindBitmap(String uri, ImageView imageView, int width, int height, boolean isRound, boolean zoom)
bindBitmap(String uri, ImageView imageView, int inSampleSize, boolean isRound, boolean zoom)
bindBitmap(String uri, ImageView imageView, boolean isRound, boolean zoom)

bindBitmap(String uri, ImageView imageView, int loadImage,
                           int errorImage, int inSampleSize, boolean isRound, boolean zoom)
//图片地址，imagView,加载中显示图片，加载失败显示图片，缩放比例，圆角，缩放
```