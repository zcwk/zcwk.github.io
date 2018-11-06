## 米域APP协议相关
唤醒APP 到指定的界面 （唤醒途径 H5 和 极光推送 ）

固定的协议 mixpace://mixpace_host/web?url=http://114.55.255.164:8093/activity/#/bridge

1.mixpace

    H5 唤醒的Scheme （后端极光推送不用管这个）
  
2.mixpace_host

    H5 唤醒的协议Host （后端极光推送不用管这个）
  
3./web 代表对应的界面 

        /web就是要打开webView界面
        /home 打开主页
      
      
## 举个栗子

    H5打开官网  mixpace://mixpace_host/web?url=http://www.mixpace.com
    
    推送打开官网  key=/web
                 url=http://www.mixpace.com
                 
    H5打开福利页面  mixpace://mixpace_host/home?index=2
    
    推送打开福利页面  key=/home
                    param=index=2
    

### 相应的协议
| 打开的界面        | H5路径    | 极光推送路径   | 
| --------   | -----  | -----   | 
| 活动详情页        | mixpace://mixpace_host/web?url=http://xxxxx&id=3456    | key= /web/activityDetail   param=url=http://xxxxx.com&id=3456      |  
| HOD活动详情页     | mixpace://mixpace_host/web?url=http://xxxxx         | key= /web/base   param=url=http://xxxxx.com          |   
| 拼团活动详情      | mixpace://mixpace_host/web?url=http://xxxxx       | key= /web/base   param=url=http://xxxxx.com         |   
| 我的活动界面      | mixpace://mixpace_host/myActivity         | key= /myActivity         |  

### 说明
    H5打开的时候记得在路径后面加入参数哦，比如 mixpace://mixpace_host/web/activityDetail?url=http://xxxxx   

