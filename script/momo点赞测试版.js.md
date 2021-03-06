 # momo点赞测试版.js
```
auto();//授权auto.js

//基础配置
var dianzancishu = 0;
var dianzanshijian = 1000;
var denglu_cishu = 0;
xuanze_xb = "男";//想看到的用户  全部、女、男
xuanze_sj = "15分钟"; //出现的时间   15分钟 1小时 1天
xuanze_nl = "全部";//出现的时间   15分钟 1小时 1天
xuanze_xz = "不限";//12星座 
xuanze_vip = 0;//是否看会员 0=不看，1=看
dengdai = 5;//默认5秒点赞一次
wait_time = 1000*dengdai;//1秒


main();
function main(){
    momozhuye();
}

function momozhuye(){
    if(text('附近动态').exists()&&text('附近的人').exists()&&text('附近直播').exists()){
        toast('陌陌首页');
        //sleep(1000);
        附近的人 = className('android.view.ViewGroup').find()[6];
        click(附近的人.bounds().centerX(),附近的人.bounds().centerY());
        sleep(2000);
        click(975,530);//点击筛选
        while(1){
            sleep(2000);
            if(text('筛选').exists()){
                if(xuanze_xb=='女')   click(339,583);
                if(xuanze_xb=='男')   click(587,583);
                sleep(1000);
                if(xuanze_sj=="3天")  click(823,836);
                if(xuanze_sj=="1天")  click(605,836);
                if(xuanze_sj=="1小时")  click(336,836);
                if(xuanze_sj=="15分钟")  click(62,836);
                sleep(1000);
                if(xuanze_vip==0){
                    if(className('android.widget.CompoundButton').findOne().checked()){
                        click(className('android.widget.CompoundButton').findOne().bounds().centerX(),className('android.widget.CompoundButton').findOne().bounds().centerY());
                    }
                }else{
                    if(!className('android.widget.CompoundButton').findOne().checked()){
                        click(className('android.widget.CompoundButton').findOne().bounds().centerX(),className('android.widget.CompoundButton').findOne().bounds().centerY());
                    }
                }
                sleep(1000);
                //点击完成
                text('完成').click();
                break;
            }   
        }
        sleep(3000);
        //收缩上面的菜单栏
        if(text('附近正在线的人').exists()){
            swipe(500,478+210,500,72,800);//收缩导航栏
        }else{
            swipe(500,478,500,72,800);
        }
        sleep(2000);
        flag = true;
        while(flag){
            sleep(3000);
            //检测附近用户是否加载
            if(id('com.immomo.momo:id/userlist_item_tv_name').exists()&& !text('已展示所有筛选结果，可选择其他筛选项').exists()){
                list = id('com.immomo.momo:id/userlist_item_tv_name').find();
                list.forEach(child=>{
                    if(child.bounds().centerY()>1590){
                        sleep(1000);
                        swipe(500,497,500,252,1000);//每次执行完滑动一次
                    }
                    if(child.bounds().width()>600){
                        toastLog('有广告:'+child.text());
                    }else{
                        click(child.bounds().centerX(),child.bounds().centerY());
                        text('对话').waitFor();
                        swipe(500,1000,500,0,1000);
                        sleep(2000);
                        if(id("feed_like_view").exists()){
                            sleep(1000);
                            click(id("feed_like_view").find()[0].bounds().centerX(),id("feed_like_view").find()[0].bounds().centerY());
                            sleep(2000);
                            dianzancishu++;
                            //当前已经点赞
                            toastLog("用户:"+child.text()+"|点赞成功,当前点赞次数:"+dianzancishu); 
                        }else{
                            toastLog("当前用户没有动态");
                        }
                        back();
                        sleep(wait_time);
                    }
                      
                });
               
            }else if (text('已展示所有筛选结果，可选择其他筛选项').exists()){
                toastLog('切换账号了');
                exit();
            }else{
                //没有加载数据
                toastLog('附近的人没有数据加载');
                continue;
            }
        }
    }
}```
