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
 *  checkAuth($appid,$appsecret,$token) 此处传入公众后台高级接口提供的appid和appsecret, 或者手动指定$token为access_token。函数将返回access_token操作令牌
 *  createMenu($data) 创建菜单 $data菜单结构详见 **[自定义菜单创建接口](http://mp.weixin.qq.com/wiki/index.php?title=自定义菜单创建接口)**
 *  getServerIp() 获取微信服务器IP地址列表 返回数组array('127.0.0.1','127.0.0.1')
 *  getMenu() 获取菜单 
 *  deleteMenu() 删除菜单 
 *  uploadMedia($data, $type) 上传多媒体文件
 *  getMedia() 获取接收到的音频、视频媒体文件 
 *  uploadArticles($data) 上传图文消息素材
 *  sendMassMessage($data) 高级群发消息
 *  sendGroupMassMessage($data) 高级群发消息（分组群发）
 *  deleteMassMessage() 删除群发图文消息
 *  getQRCode($scene_id,$type=0,$expire=1800) 获取推广二维码ticket字串 
 *  getQRUrl($ticket) 获取二维码图片地址
 *  getShortUrl($long_url) 长链接转短链接接口
 *  getUserList($next_openid) 批量获取关注用户列表 
 *  getUserInfo($openid) 获取关注者详细信息 
 *  updateUserRemark($openid,$remark) 设置用户备注名
 *  getGroup() 获取用户分组列表 
 *  getUserGroup($openid) 获取用户所在分组
 *  createGroup($name) 新增自定分组 
 *  updateGroup($groupid,$name) 更改分组名称 
 *  updateGroupMembers($groupid,$openid) 移动用户分组  
 *  sendCustomMessage($data) 发送客服消息  
 *  getOauthRedirect($callback,$state,$scope) 获取网页授权oAuth跳转地址  
 *  getOauthAccessToken() 通过回调的code获取网页授权access_token  
 *  getOauthRefreshToken($refresh_token) 通过refresh_token对access_token续期  
 *  getOauthUserinfo($access_token,$openid) 通过网页授权的access_token获取用户资料  
 *  getOauthAuth($access_token,$openid)  检验授权凭证access_token是否有效
 *  getSignature($arrdata,'sha1') 生成签名字串  
 *  generateNonceStr($length) 获取随机字串  
 *  createPackage($out_trade_no,$body,$total_fee,$notify_url,$spbill_create_ip,$fee_type=1,$bank_type="WX",$input_charset="UTF-8",$time_start="",$time_expire="",$transport_fee="",$product_fee="",$goods_tag="",$attach="") 生成订单package字符串  
 *  getPaySign($package, $timeStamp, $nonceStr) 支付签名(paySign)生成方法  
 *  checkOrderSignature($orderxml='') 回调通知签名验证  
 *  sendPayDeliverNotify($openid,$transid,$out_trade_no,$status=1,$msg='ok') 发货通知  
 *  getPayOrder($out_trade_no) 查询订单信息  
 *  getAddrSign($url, $timeStamp, $nonceStr, $user_token='') 获取收货地址JS的签名
 *  sendTemplateMessage($data) 发送模板消息
 *  getCustomServiceMessage($data) 获取多客服会话记录
 *  transfer_customer_service($customer_account) 转发多客服消息
 *  getCustomServiceKFlist() 获取多客服客服基本信息
 *  getCustomServiceOnlineKFlist() 获取多客服在线客服接待信息
 *  querySemantic($uid,$query,$category,$latitude=0,$longitude=0,$city="",$region="") 语义理解接口 参数含义及返回的json内容请查看 **[微信语义理解接口](http://mp.weixin.qq.com/wiki/index.php?title=语义理解)**
 

反馈或贡献代码
------------
您可以在[这里](https://github.com/lujian/yii2-wechat/issues)给我提出在使用中碰到的问题或Bug.
我会在第一时间回复您并修复.

您也可以 发送邮件254461627@qq.com给我并且说明您的问题.

如果你有更好代码实现,请fork项目并发起您的pull request.我会及时处理. 感谢!
