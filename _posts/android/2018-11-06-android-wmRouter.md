## 米域APP协议相关
唤醒APP 到指定的界面 （唤醒途径 H5 和 极光推送 ）

固定的协议 mixpace://mixpace_host/web/base?url=http://114.55.255.164:8093/activity/#/bridge

1.mixpace

    H5 唤醒的Scheme （后端极光推送不用管这个）
  
2.mixpace_host

    H5 唤醒的协议Host （后端极光推送不用管这个）
  
3./web/base 分两级
  
    1）第一级 /web 代表对应的界面 
  
            比如/web就是要打开webView界面
      
            /home 打开主页
      
    2）第二级 /base 代表不同的功能 
  
            比如/base 仅仅是打开一个网页而已
      
            /mine 打开主页的我的tab
      
## 举个栗子

    H5打开官网  mixpace://mixpace_host/web/base?url=http://www.mixpace.com
    
    推送打开官网  key=/web/base
                 url=http://www.mixpace.com
                 
    H5打开福利页面  mixpace://mixpace_host/home/welfare
    
    推送打开福利页面  key=/home/welfare
    

### 相应的协议
| 打开的界面        | H5路径    | 极光推送路径   | 
| --------   | -----  | -----   | 
| 活动详情页        | mixpace://mixpace_host/web/activityDetail?url=http://xxxxx    | key= /web/activityDetail   param=url=http://xxxxx.com&id=3456      |  
| HOD活动详情页     | mixpace://mixpace_host/web/base?url=http://xxxxx         | key= /web/base   
param=url=http://xxxxx.com&id=3456          |   
| 拼团活动详情      | mixpace://mixpace_host/web/base?url=http://xxxxx       | key= /web/base   
param=url=http://xxxxx.com&id=3456         |   
| 我的活动界面      | mixpace://mixpace_host/activity/myActivity         | key= /activity/myActivity         |  

### 说明
    H5打开的时候记得在路径后面加入参数哦，比如 mixpace://mixpace_host/web/activityDetail?url=http://xxxxx   

