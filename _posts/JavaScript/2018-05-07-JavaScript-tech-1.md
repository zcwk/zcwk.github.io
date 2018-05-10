---

layout: post

title: 微信小程序支付的坑 

category: JavaScript


tags: Blog


keywords: JavaScript,微信小程序

description:

---



## 小程序支付的坑

### 发起支付后报"支付验证签名失败"

```javascript
wx.requestPayment({
      'appId': res.appId,
      'timeStamp': res.timestamp.toString(),
      'nonceStr': res.noncestr,
      'package': res.package,
      'signType': res.signType,
      'paySign': res.paySign,
      'success': function (s_res) {
        return typeof success == "function" && success()
      },
      'fail': function (f_res) {
        return typeof fail == "function" && fail(f_res)
      },
      'complete': function (res) {
        if (res && res.errMsg == 'requestPayment:cancel') {
          return typeof fail == "function" && fail(f_res)
        }
      }
    })
```

认真确认一下传参的大小写。如果没有错的话。那就是服务器的生成paySign的问题。我就遇到这个坑。服务哥们说不是他的问题。然后我就让他去验证一下。[验证地址](https://pay.weixin.qq.com/wiki/doc/api/jsapi.php?chapter=20_1)

通过验证果然是服务端生成paySign大小写没注意。

如果不是大小写问题的话。那就重新去商户平台-》账户中心》 重新生成Key


