
### 使用方法
```java
HttpUtils.doGetStr(url) or HttpUtils.doPostStr(url);
```
以上url即为接口访问地址，调用此方法访问接口，接口返回类型为json

#### 传递参数的两种方式
- 1、StringEntity

```java
    HttpPost httpPost = new HttpPost(url);  
    //param参数，可以为param="key1=value1&key2=value2"的一串字符串,或者是jsonObject 
     String param1="key1=value1&key2=value2"
    JSONObject param2= new JSONObject();  
    param2.put("key1", "value1");  
    param2.put("key2t"," value2");  
    StringEntity stringEntity = new StringEntity(param1);  
    StringEntity stringEntity = new StringEntity(param2.toString());  
    stringEntity.setContentType("application/x-www-form-urlencoded");
    httpPost.setEntity(stringEntity);  
    HttpClient client = new DefaultHttpClient();   
    HttpResponse httpResponse = client.execute(httpPost);  
    String result = EntityUtils.toString(httpResponse.getEntity(), HTTP.UTF_8);  
``` 
 

- 2、UrlEncodedFormEntity
```java
    List<NameValuePair> pairs = new ArrayList<NameValuePair>(); 
    NameValuePair pair1 = new BasicNameValuePair("supervisor", supervisorEt.getEditableText().toString());  
    NameValuePair pair2 = new BasicNameValuePair("content", superviseContentEt.getEditableText().toString());  
    NameValuePair pair3 = new BasicNameValuePair("userId", String.valueOf(signedUser.getId()));  
    pairs.add(pair1);  
    pairs.add(pair2);  
    pairs.add(pair3);  
    httpPost.setEntity(new UrlEncodedFormEntity(pairs, HTTP.UTF_8)) 
```
