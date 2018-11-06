## 米域APP协议相关
唤醒APP 到指定的界面 （唤醒途径 H5 和 极光推送 ）

固定的协议 mixpace://mixpace_host/web/base?url=http://114.55.255.164:8093/activity/#/bridge

1.mixpace

    H5 唤醒的Scheme （后端极光推送不用管这个）
  
2.mixpace_host

    H5 唤醒的协议Host （后端极光推送不用管这个）
  
3./web/base

    分两级
  
  1）第一级 /web 代表对应的界面 
  
      比如/web就是要打开webView界面
      
      /home 打开主页
      
  2）第二级 /base 代表不同的功能 
  
      比如/base 仅仅是打开一个网页而已
      
      /mine 打开主页的我的tab
      
### H5唤醒


### 极光推送唤醒

