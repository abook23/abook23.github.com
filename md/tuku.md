###图库
```java
调用图库
Intent intent = new Intent(context, PhotoActivity.class);
intent.putExtra(PhotoActivity.CHECK_COUNT, Integer.valueOf(editText.getText().toString()));
startActivityForResult(intent, 1);

照片返回
@Override
protected void onActivityResult(int requestCode, int resultCode, Intent data) {
    super.onActivityResult(requestCode, resultCode, data);
    if (requestCode == 1 && resultCode == Activity.RESULT_OK) {
        ArrayList<String> datas = data.getStringArrayListExtra(PhotoActivity.DATA);
        showImage(datas);
    }
}

```