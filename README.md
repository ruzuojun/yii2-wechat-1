yii2-wechat
===============


环境条件
------------
- >= php5.4
- Yii2

安装
------------

您可以使用composer来安装, 添加下列代码在您的``composer.json``文件中并执行``composer update``操作

```json
{
    "require": {
       "lujian/yii2-wechat": "dev-master"
    }
}
```

或

```
composer require "lujian/yii2-wechat:*"
```

使用示例
------------
在使用前,请先参考微信公众平台的[开发文档](http://mp.weixin.qq.com/wiki/index.php?title=%E9%A6%96%E9%A1%B5)

Wechat定义方式
```php
//在config/web.php配置文件中定义component配置信息
'components' => [
  .....
  'wechat' => [
    'class' => 'lujian\wechat\Wechat',
    'config' => [
        'token'=>'tokenaccesskey', //填写你设定的key
        'encodingaeskey'=>'encodingaeskey', //填写加密用的EncodingAESKey
        'appid'=>'wxdk1234567890', //填写高级调用功能的app id, 请在微信开发模式后台查询
        'appsecret'=>'xxxxxxxxxxxxxxxxxxx', //填写高级调用功能的密钥
        'partnerid'=>'88888888', //财付通商户身份标识，支付权限专用，没有可不填
        'partnerkey'=>'', //财付通商户权限密钥Key，支付权限专用
        'paysignkey'=>'' //商户签名密钥Key，支付权限专用
    ]
  ]
  ....
]
// 全局公众号sdk使用
$wechat = Yii::$app->wechat;




```

反馈或贡献代码
------------
您可以在[这里](https://github.com/lujian/yii2-wechat/issues)给我提出在使用中碰到的问题或Bug.
我会在第一时间回复您并修复.

您也可以 发送邮件254461627@qq.com给我并且说明您的问题.

如果你有更好代码实现,请fork项目并发起您的pull request.我会及时处理. 感谢!
