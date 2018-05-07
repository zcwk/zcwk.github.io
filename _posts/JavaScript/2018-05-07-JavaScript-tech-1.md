---

layout: post
title: 微信小程序支付的坑 category: JavaScript
tags: Blog
keywords: JavaScript,微信小程序

## description:

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
