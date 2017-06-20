# GetToken
不需要依赖服务端直接从 Android 端获取 [融云](http://rongcloud.cn) token 的 Jcenter 

## 使用

```java
dependencies {

    compile 'cn.rongcloud.android:getrongcloudtoken:1.0.0'

}
```

## 示例

``` java
public class MainActivity extends AppCompatActivity {

    public static final String RONG_KEY = "xxx";// 融云key
    public static final String RONG_SECRET = "xxx";// 融云密钥 secret

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }

    public void getToken(View view) {
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
    }

}
```

## 警告⚠️
- 建议此种方式只在测试环境使用。
- 融云不建议直接在客户端向融云获取 token ,  此种行为导致 app secret 暴露在客户端有被反编译破解的可能！
- 关于本开源项目的解释权归 [融云](http://rongcloud.cn) 所有。


            
