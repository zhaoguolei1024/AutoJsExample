 # leimu.js
```
setInterval(function gongneng() {
    launchApp("����");
    sleep(1500)
    text('ͬ��').waitFor();
    while (!click("ͬ��"));
    var _id = id("live_mark").visibleToUser(true).findOne().parent();
    _id.click();
    sleep(4000);
    //var b = id("live_close").findOne();
    var n = id("timer_view").findOne(4000);
    if (n != null) {
        id("background_view_normal").findOne().click();
        text("4���Ӻ�").waitFor();
        var t = setInterval(function() {
        id("live_red_packet_pre_snatch_state_view").findOne(20).click();
		sleep(150);
        if (textContains("�����ˣ����������").findOne(1) != null) {
             clearInterval(t);
			 openAppSetting(getPackageName("����"));
             text("ǿ��ֹͣ").findOne().click();
             text("ȷ��").findOne().click();
             sleep(2000);
                                                                      }
		else if(textContains("ֱ���ѽ���").findOne(1) != null){
			 clearInterval(t);
			 openAppSetting(getPackageName("����"));
             text("ǿ��ֹͣ").findOne().click();
             text("ȷ��").findOne().click();
             sleep(2000);
			                                                     }
                                          }, 500);

                  }else{
        //������ʾû���ҵ�
        toast("û�к����������");
        sleep(1200);
        openAppSetting(getPackageName("����"));
        text("ǿ��ֹͣ").findOne().click();
        text("ȷ��").findOne().click();
        sleep(2000);
    }

}, 5000);```
