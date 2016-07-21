#http网络请求


##同步请求
###GET
```java
HttpInfo httpInfo = HttpUtils.get("http://news.baidu.com/ns?cl=2&rn=20&tn=news&word=豌豆荚%20开发者");
```

###POST
```java
HashMap<String, Object> hashMap = new HashMap<>();
hashMap.put("from", "bdwz");
HttpInfo httpInfo = HttpUtils.post("https://www.baidu.com/", hashMap);
```

###异步请求
方式1
```java
    @Override
    public void login(UserInfo userInfo, HttpRequestListener<RootBean> listener) {
        HttpThreadUtils.post(ServiceURL.login)
                .addParams("userName", userInfo.getName())
                .addParams("password", userInfo.getUserId())
                .setHttpRequestListener(RootBean.class, listener)
                .execute();
    }
```
方式2
```java
    @Override
    public void register(UserInfo userInfo, HttpRequestListener<UserInfo> listener) {
        HttpThreadPool<UserInfo> httpThreadPool = new HttpThreadPool<UserInfo>() {
            @Override
            protected UserInfo doInBackground(String result) {
                RootBean rootBean = getRootBean(result);//统一处理底层
                UserInfo u = JsonUtils.jsonToBean(rootBean.getContent(), UserInfo.class);
                return u;
            }
        };
        httpThreadPool.post(ServiceURL.login)
                .addParams("userName", userInfo.getName())
                .addParams("password", userInfo.getUserId())
                .setHttpRequestListener(listener)
                .execute();
    }
```
方式三
```java
        new AsyncThreadPool<String, Integer, UserInfo>() {
            @Override
            protected UserInfo doInBackground(String... params) {
                HttpInfo httpInfo = HttpUtils.get("");
                HttpUtils.post("", null);
                return null;
            }

            @Override
            protected void onPostExecute(UserInfo userInfo) {
                super.onPostExecute(userInfo);
            }
        }.execute();
```
####自定义线程池+回调 HttpThreadPool<T>
```java
    private void http_1() {
        HttpTask httpTask = new HttpTask();

        //get
        httpTask.get("url");
        //参数
        httpTask.addParams("key", "values");
        //map 参数
        httpTask.setParams(null);
        //回调监听---
        //setRequestCode 默认 0
        //当有多个网络请求时，是用区分是那个的返回
        httpTask.setHttpRequestListener(this).setRequestCode(0);
        //执行
        httpTask.execute();

        //post
        httpTask.post("url").setParams(null);
        httpTask.setHttpRequestListener(this).setRequestCode(0);
        httpTask.execute();

    }
	
	
	//setHttpRequestListener(this).setRequestCode(0) 的回调
    @Override
    public void onHttpSuccess(UserInfo userInfo, int requestCode) {
		//网络请求完成后---主线程
    }

    @Override
    public void onHttpError(String msg, int resultCode, int requestCode) {

    }
	
	
	/**
     * 线程池 网络请求 封装
     * 为了 方便大部分用户 使用方法 同 AsyncTask
     */
	private class HttpTask extends HttpThreadPool<UserInfo> {
        @Override
        protected void onPreExecute() {
            super.onPreExecute();
            //异步请求之前
        }

        @Override
        protected UserInfo doInBackground(String result) {
            //网络请求后的逻辑处理
            //比如 json 解析 ,数据库 操作等
            // return 为 网络回调监听的返回值
            UserInfo userInfo = JsonUtils.jsonToBean(result,UserInfo.class);
            return userInfo;
        }

        @Override
        protected void onPostExecute(UserInfo userInfo) {
            super.onPostExecute(userInfo);
            //网络请求完成
        }
    }
```