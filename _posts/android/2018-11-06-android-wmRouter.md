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
| 活动详情页        | mixpace://mixpace_host/web?url=http://xxxxx&id=3456&share=1    | key= "/web" param="url=http://xxxxx.com&id=3456&share=1"      |  
| HOD活动详情页     | mixpace://mixpace_host/web?url=http://xxxxx         | key= "/web"   param="url=http://xxxxx.com&id=3456&share=1"          |   
| 拼团活动详情      | mixpace://mixpace_host/web?url=http://xxxxx?token=1       | key= "/web"   param="url=http://xxxxx.com?token=1&id=3456&share=1"          |   
| 我的活动界面      | mixpace://mixpace_host/myActivity         | key= "/myActivity"         |  
| 我的优惠券      | mixpace://mixpace_host/myCoupon?account_id=34        | key= "/myCoupon" param="account_id=34&id=3456&share=1"         |
| 团推优惠券      | mixpace://mixpace_host/teamCoupon?account_id=54      | key= "/teamCoupon" param="account_id=54&id=3456&share=1"        |
| 团队主页     | mixpace://mixpace_host/myTeam?account_id=54      | key= "/myTeam" param="account_id=54&id=3456&share=1"        |
| 团队信息编辑页面      | mixpace://mixpace_host/TeamEdit?account_id=54      | key= "/TeamEdit" param="account_id=54&id=3456&share=1"        |
### 说明
    参数id 表示活动id
    参数share 表示web界面右上角是要有分享按钮
    参数token 表示需要在url后面加token

