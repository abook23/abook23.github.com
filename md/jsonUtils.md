

```java
static <T> List<T>	fromJsonArray(List<?> list, Class<T> class1) 
static <T> List<T>	fromJsonArray(String json, Class<T> clazz) 
static <T> List<T>	jsonToBean(List<?> list, Class<T> class1) 
static <T> T		jsonToBean(Object object, Class<T> class1) 
static <T> T		jsonToBean(String json, Class<T> class1)
static HashMap<String,Object>	jsonToHasMap(org.json.JSONObject jsonObject)
static List<Object>	jsonToList(org.json.JSONArray jsonArray)
static String	toJson(Object object) 
```