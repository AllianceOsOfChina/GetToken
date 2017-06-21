# GetToken
不需要依赖服务端直接从 Android 端获取 [融云](http://rongcloud.cn) token 的 Jcenter 

## 关于

[token & appkey & secret](http://www.rongcloud.cn/docs/quick_start.html#development)

## 使用

```java
dependencies {

    compile 'cn.rongcloud.android:getrongcloudtoken:1.0.0'

}
```

## 权限

```xml
    <uses-permission android:name="android.permission.INTERNET" />
```

## 示例

``` java
TokenManager.getInstance(this).getTokenById(RONG_KEY, RONG_SECRET, "rongcloudgettoken", new TokenManager.OnResultTokenListener() {
            @Override
            public void onResult(TokenResult tokenResult) {
                if (tokenResult.getCode() == 200) {
                    Log.e("MainActivity", tokenResult.getToken());
                    Toast.makeText(MainActivity.this, "token is :" + tokenResult.getToken(), Toast.LENGTH_SHORT).show();
                } else {
                    Log.e("MainActivity", tokenResult.getErrorMessage());
                    Toast.makeText(MainActivity.this, "error is :" + tokenResult.getErrorMessage(), Toast.LENGTH_SHORT).show();
                }
            }
        });
```

## API

Mothed | param1 | param2 | param3 | param4 | param5 | param6 
----|------|---- | ---- | ---- | ---- | ---- 
getTokenById | String:appKey  | String:appSecret | String:userId | OnResultTokenListener |  |  
getTokenByUserInfo | String:appKey  | String:appSecret | String:userId | String:name | String:portraitUri | OnResultTokenListener 





## 警告⚠️
- 建议此种方式只在测试环境使用。
- 融云不建议直接在客户端向融云获取 token ,  此种行为导致 app secret 暴露在客户端有被反编译破解的可能！
- 关于本开源项目的解释权归 [融云](http://rongcloud.cn) 所有。


            
