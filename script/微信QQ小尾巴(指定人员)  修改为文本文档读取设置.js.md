 # 微信QQ小尾巴(指定人员)  修改为文本文档读取设置.js
```
"auto"
var QQ自定义列表 = new Array();
var 微信自定义列表 = new Array();

//更新内容： 支持 自定义好友（或者群）小尾巴 。

//默认结束标志为 两个换行符，即连续输入两次回车键。
//最近修改时间：2018年2月28日 12:00
//请在手机QQ中：设置→辅助功能→回车键发送消息  设置为关闭。


//———————————————— 文本输入结束 标志字符串 ——————————————————
var QQ结束标志 = "\n\n";
var 微信结束标志 = "\n\n";
//默认 连续输入两次回车键  发送消息。


//———————————————————— 通用小尾巴设置 ————————————————————————
function QQ通用小尾巴() {
  var date = new Date();
  var month = "0" + (date.getMonth() + 1);
  month = month.substr(-2);
  var day = "0" + date.getDate();
  day = day.substr(-2);
  var time = date.toTimeString().substr(0, 8);
  time = month + "月" + day + "日 " + time;
  var 充电状态 = "🔋";
  if (device.isCharging()) {
    充电状态 = "⚡";
  }
    eval(xiaoweiba);
    return QQ小尾巴;
}

function 微信通用小尾巴() {
  var date = new Date();
  var month = "0" + (date.getMonth() + 1);
  month = month.substr(-2);
  var day = "0" + date.getDate();
  day = day.substr(-2);
  var time = date.toTimeString().substr(0, 8);
  time = month + "月" + day + "日 " + time;
  var 充电状态 = "🔋";
  if (device.isCharging()) {
    充电状态 = "⚡";
  }
    eval(xiaoweiba);
      return 微信小尾巴;
}


 

 

//——————————————————————控件id设置——————————————————————————
var QQ文本框id = "input";
var QQ昵称id = "title";

var 微信文本框id = "aa1";
var 微信昵称id = "h5";

//小尾巴在文件中
peizhi="/sdcard/QQ微信小尾巴.txt"
//以附加模式打开文件
file = open(peizhi, "a");
file.close();
file = open(peizhi, "r")
//toast (file.readline()==null)
if (file.readline()==null)
{
    file.close();

  file = open(peizhi,"w");
   // file.write("nih");
 file.writeline("var 内存='RAM空'+Math.floor(device.getAvailMem()/1024/1024)+'/'+Math.floor(device.getTotalMem()/1024/1024)+'M';");
 file.writeline("var QQ小尾巴 = '/n📱🐔' + time + '/n📱🐔'+device.brand +'安卓' +device.release+'/n📱🐔'+ 内存 +'/n📱🐔剩余电量'+充电状态+ device.getBattery() + '%';");
 file.writeline("var 微信小尾巴 = '/n📱🐔' + time + '/n📱🐔'+ device.brand +'安卓' +device.release+'/n📱🐔'+ 内存 +'/n📱🐔剩余电量'+充电状态+ device.getBattery() + '%';");
file.close();
}
else
 {
        file.close();
  }
//以读取模式打开文件
file = open(peizhi, "r")
var xiaoweiba=file.readline();
for each(line in file.readlines()){
 xiaoweiba=xiaoweiba + line;
}
file.close()
//toast(xiaoweiba)
//以上是 小尾巴从文件读取
//自定义小尾巴也在文件中
peizhi="/sdcard/QQ微信自定义尾巴.txt"
//以附加模式打开文件
file = open(peizhi, "a");
file.close();
file = open(peizhi, "r")
//toast (file.readline()==null)
if (file.readline()==null)
{
    file.close();

  file = open(peizhi,"w");
   // file.write("nih");
 file.writeline("QQ备注#QQ小尾巴='自定义QQ小尾巴';");
 file.writeline("微信备注#微信小尾巴='自定义微信小尾巴';");
 
    file.close();
}
else
 {
        file.close();
  }
//以读取模式打开文件
file = open(peizhi, "r")
QQjsq =0
微信jsq=0
QQ自定义={}
微信自定义={}
for each(line in file.readlines()){
   s1=line
 if(s1.substr(0,2)=="QQ")
    {
        QQjsq=QQjsq+1
        a=s1.indexOf("#")
        s2=s1.substr(2,a-2)
        s3=s1.substr(a+1,s1.length)
       // toast(s2+"   "+s3)
        QQ自定义列表[QQjsq]=s2
        QQ自定义[QQjsq]=s2
        QQ自定义[s2]=s3
     }
   if (s1.substr(0,2)=="微信")
        {
            微信jsq=微信jsq+1
            
        a=s1.indexOf("#")
        s2=s1.substr(2,a-2)
        s3=s1.substr(a+1,s1.length)
        //toast(s2+"  "+s3)
        微信自定义列表[微信jsq]=s2
        微信自定义[微信jsq]=s2
        微信自定义[s2]=s3
        }
}
file.close()
//自定义小尾巴
//—————————————————————————— 主程序 ——————————————————————————
while (true) {
  sleep(300);
  var 当前活动 = currentActivity();
  switch (true) {

    //—————————————————————— QQ 部分 ————————————————————————
    case 当前活动 == "com.tencent.mobileqq.activity.SplashActivity" || 当前活动 == "com.tencent.mobileqq.activity.ChatActivity":
      if (id(QQ文本框id).editable(true).textEndsWith(QQ结束标志).exists()) {
        var QQ文本框内容 = id(QQ文本框id).editable(true).find().get(0).text();
        QQ文本框内容 = QQ文本框内容.substr(0, QQ文本框内容.length - QQ结束标志.length);
        if (/表情\//.test(QQ文本框内容)) {
          QQ文本框内容 = 表情1查找(QQ文本框内容);
        }
        if (/\[.{1,3}\]/.test(QQ文本框内容)) {
          QQ文本框内容 = 表情3查找(QQ文本框内容);
        }
        if (/ /.test(QQ文本框内容)) {
          QQ文本框内容 = 表情2查找(QQ文本框内容);
        }

        var 昵称 = id(QQ昵称id).className("android.widget.TextView").find().get(0).text();
        var 序号 = QQ自定义列表.indexOf(昵称);
        if (序号 == -1) {
          var QQ小尾巴 = QQ通用小尾巴();
        } else {
            var date = new Date();
  var month = "0" + (date.getMonth() + 1);
  month = month.substr(-2);
  var day = "0" + date.getDate();
  day = day.substr(-2);
  var time = date.toTimeString().substr(0, 8);
  time = month + "月" + day + "日 " + time;
  var 充电状态 = "🔋";
  if (device.isCharging()) {
    充电状态 = "⚡";
  }
            eval(QQ自定义[昵称])
         // QQ小尾巴 = eval("QQ自定义尾巴" + 序号 + "()");
          序号 = -1;
        }
        setText(QQ文本框内容 + QQ小尾巴);

        while (!click("发送")) {
          sleep(100)
        }
      }
      break


      //—————————————————————————— 微信 部分 ——————————————————————————
    case 当前活动 == "com.tencent.mm.ui.chatting.ChattingUI" || 当前活动 == "com.tencent.mm.ui.LauncherUI":
      if (id(微信文本框id).editable(true).textEndsWith(微信结束标志).exists()) {
        var 微信文本框内容 = id(微信文本框id).editable(true).textEndsWith(微信结束标志).find().get(0).text();
        微信文本框内容 = 微信文本框内容.substr(0,微信文本框内容.length - 微信结束标志.length);
        var 昵称 = id(微信昵称id).className("android.widget.TextView").find().get(0).text();
        var 序号 = 微信自定义列表.indexOf(昵称);
        if (序号 == -1) {
          var 微信小尾巴 = 微信通用小尾巴();
        } else {
            var date = new Date();
  var month = "0" + (date.getMonth() + 1);
  month = month.substr(-2);
  var day = "0" + date.getDate();
  day = day.substr(-2);
  var time = date.toTimeString().substr(0, 8);
  time = month + "月" + day + "日 " + time;
  var 充电状态 = "🔋";
  if (device.isCharging()) {
    充电状态 = "⚡";
  }
         eval(微信自定义[昵称])
          //  var 微信小尾巴 = eval("微信自定义尾巴" + 序号 + "()");
          序号 = -1;
        }
        setText(微信文本框内容 + 微信小尾巴);
        
        while (!click("发送")) {
          sleep(100)
        }
      }
      break

    default:
      sleep(700);
      break
  }
}
//—————————————————————— 主程序结束 ————————————————————




//——————————————————————————QQ表情修正函数——————————————————————————

//————————————————————QQ经典小表情修正——————————————————————
function 表情1替换(表情名称) {
  var 表情代码 = "(+	j# ! \nQR%2*S\"1T'NUVW.X,Y0Z)$[3¤«¥¦¡§ª¬­¨¯<=\\]£B:9J;PFM>DKL-45678?IHA^@&/_G`abcdOefghilmnptuvwx{´¸°±¶³¹ º»¼½¾¿ÀÁÂÃÄÅÆÇÈ";
  var 表情名 = ["/微笑", "/撇嘴", "/色", "/发呆", "/得意", "/流泪", "/害羞", "/闭嘴", "/睡", "/尴尬", "/发怒", "/调皮", "/呲牙", "/惊讶", "/难过", "/酷", "/冷汗", "/抓狂", "/吐", "/偷笑", "/可爱", "/白眼", "/傲慢", "/饥饿", "/困", "/惊恐", "/流汗", "/憨笑", "/悠闲", "/奋斗", "/咒骂", "/疑问", "/嘘...", "/晕", "/折磨", "/衰", "/骷髅", "/敲打", "/再见", "/擦汗", "/抠鼻", "/鼓掌", "/糗大了", "/坏笑", "/左哼哼", "/右哼哼", "/哈欠", "/鄙视", "/委屈", "/快哭了", "/阴险", "/亲亲", "/吓", "/可怜", "/眨眼睛", "/doge", "/泪奔", "/无奈", "/托腮", "/卖萌", "/斜眼笑", "/惊喜", "/骚扰", "/小纠结", "/我最美", "/菜刀", "/西瓜", "/啤酒", "/篮球", "/乒乓", "/茶", "/咖啡", "/饭", "/猪头", "/玫瑰", "/凋谢", "/示爱", "/爱心", "/心碎", "/蛋糕", "/闪电", "/炸弹", "/刀", "/足球", "/瓢虫", "/便便", "/月亮", "/太阳", "/礼物", "/拥抱", "/赞", "/踩", "/握手", "/胜利", "/抱拳", "/勾引", "/拳头", "/差劲", "/爱你", "/NO", "/OK", "/爱情", "/飞吻", "/跳跳", "/发抖", "/怄火", "/转圈", "/磕头", "/回头", "/跳绳", "/挥手", "/激动", "/街舞", "/献吻", "/左太极", "/右太极", "/双喜", "/鞭炮", "/灯笼", "/K歌", "/喝彩", "/祈祷", "/爆筋", "/棒棒糖", "/喝奶", "/飞机", "/钞票", "/药", "/手枪", "/蛋", "/红包", "/河蟹", "/羊驼", "/菊花", "/幽灵", "/大笑", "/不开心", "/冷漠", "/呃", "/好棒", "/拜托", "/点赞", "/无聊", "/托脸", "/吃", "/送花", "/害怕", "/花痴", "/小样儿", "/飙泪", "/我不看", "/啵啵", "/糊脸", "/拍头", "/扯一扯", "/舔一舔", "/蹭一蹭", "/拽炸天", "/顶呱呱", "/抱抱", "/暴击", "/开枪", "/撩一撩", "/拍桌", "/拍手", "/恭喜"];
  var a = 表情名.indexOf(表情名称);
  switch (a) {
    case -1:
      return false;
      break

    default:
      return 表情代码.substr(2 * a, 2)
  }
}

function 表情1查找(文本内容) {
  var 表情 = "";
  var 检索符号 = ["表情/", "/"];
  for (var n = 0; n < 2; n++) {
    var 文本内容分割 = 文本内容.split(检索符号[n]);
    if (文本内容分割.length > 1) {
      for (var i = 1; i < 文本内容分割.length; i++) {
        for (var s = 1; s <= 文本内容分割[i].length && s < 5; s++) {
          表情 = 表情1替换("/" + 文本内容分割[i].substr(0, s));
          if (表情) {
            文本内容分割[i] = 表情 + 文本内容分割[i].substr(s);
            break;
          }
        }
        if (!表情) {
          文本内容分割[i] = 检索符号[n] + 文本内容分割[i]
        }
        表情 = false;
      }
      文本内容 = 文本内容分割.join("");
    }
  }
  return 文本内容
}


//————————————————————部分 Emoji 表情修正——————————————————
function 表情2替换(表情名) {
  var 表情名列表 = ["大哭", "嘿嘿", "吐舌", "呲牙", "淘气", "可爱", "媚眼", "花痴", "失落", "高兴", "哼哼", "不屑", "瞪眼", "飞吻", "大哭", "害怕", "激动", "拳头", "厉害", "向上", "鼓掌", "胜利", "鄙视", "合十", "好的", "向左", "向右", "向上", "向下", "眼睛", "鼻子", "嘴唇", "耳朵", "米饭", "意面", "拉面", "饭团", "刨冰", "寿司", "蛋糕", "起司", "汉堡", "煎蛋", "薯条", "啤酒", "干杯", "高脚杯", "咖啡", "苹果", "橙子", "草莓", "西瓜", "药丸", "吸烟", "圣诞树", "玫瑰", "庆祝", "椰子树", "礼物", "蝴蝶结", "气球", "海螺", "戒指", "炸弹", "皇冠", "铃铛", "星星", "闪光", "吹气", "水", "火", "奖杯", "钱", "睡觉", "闪电", "脚印", "便便", "打针", "热", "文件", "钥匙", "锁", "飞机", "列车", "汽车", "自行车", "骑马", "火箭", "公交", "船", "妈妈", "爸爸", "女孩", "男孩", "猴", "章鱼", "猪", "骷髅", "小鸡", "树懒", "牛", "公鸡", "青蛙", "幽灵", "虫", "鱼", "狗", "老虎", "天使", "企鹅", "海豚", "老鼠", "帽子", "连衣裙", "口红", "云朵", "晴天", "雨天", "月亮", "雪人", "正确", "错误", "问好", "叹号", "电话", "相机", "手机", "电脑", "摄影机", "话筒", "手枪", "光碟", "爱心", "扑克", "麻将"];

  var 表情列表 = ["😭", "😊", "😝", "😁", "😜", "☺", "😉", "😍", "😔", "😄", "😏", "😒", "😳", "😘", "😭", "😱", "😂", "👊", "👍", "☝", "👏", "✌", "👎", "🙏", "👌", "👈", "👉", "👆", "👇", "👀", "👃", "👄", "👂", "🍚", "🍝", "🍜", "🍙", "🍧", "🍣", "🎂", "🍞", "🍔", "🍳", "🍟", "🍺", "🍻", "🍸", "☕", "🍎", "🍊", "🍓", "🍉", "💊", "🚬", "🎄", "🌹", "🎉", "🌴", "💝", "🎀", "🎈", "🐚", "💍", "💣", "👑", "🔔", "⭐", "✨", "💨", "💦", "🔥", "🏆", "💰", "💤", "⚡", "👣", "💩", "💉", "♨", "📫", "🔑", "🔒", "✈", "🚄", "🚗", "🚲", "🐎", "🚀", "🚌", "⛵", "👩", "👨", "👧", "👦", "🐵", "🐙", "🐷", "💀", "🐤", "🐨", "🐮", "🐔", "🐸", "👻", "🐛", "🐠", "🐶", "🐯", "👼", "🐧", "🐳", "🐭", "👒", "👗", "💄", "☁", "☀", "☔", "🌙", "⛄", "⭕", "❌", "❔", "❕", "☎", "📷", "📱", "💻", "🎥", "🎤", "🔫", "💿", "💓", "♣", "🀄"];

  var 表情 = 表情名列表.indexOf(表情名);
  if (表情 != -1) {
    return 表情列表[表情];
  } else {
    return false;
  }
}

function 表情2查找(文本内容) {
  var 检索符号 = " ";
  var 文本内容分割 = 文本内容.split(检索符号);
  if (文本内容分割.length > 1) {
    for (var i = 0; i < 文本内容分割.length - 1; i++) {
      var 表情 = false;
      var s = 文本内容分割[i].length;
      var n = "";
      if (s > 0) {
        n = Math.min(s, 3) * (-1);
        for (; n < 0; n++) {
          表情 = 表情2替换(文本内容分割[i].substr(n));
          if (表情) {
            文本内容分割[i] = 文本内容分割[i].substr(0, s + n) + 表情;
            break
          }
        }
      }
      if (!表情) {
        文本内容分割[i] += 检索符号;
      }
    }
    文本内容 = 文本内容分割.join("");
  }
  return 文本内容;
}


//—————————————————————————— 嗷大喵 小表情修正——————————————————————
function 表情3替换(表情名) {
  var 表情名列表 = ["\[拜拜\]", "\[鄙视\]", "\[菜刀\]", "\[沧桑\]", "\[馋了\]", "\[吃惊\]", "\[微笑\]", "\[得意\]", "\[嘚瑟\]", "\[瞪眼\]", "\[震惊\]", "\[鼓掌\]", "\[害羞\]", "\[好的\]", "\[惊呆了\]", "\[静静看\]", "\[可爱\]", "\[困\]", "\[脸红\]", "\[你懂的\]", "\[期待\]", "\[亲亲\]", "\[伤心\]", "\[生气\]", "\[摇摆\]", "\[帅\]", "\[思考\]", "\[震惊哭\]", "\[痛心\]", "\[偷笑\]", "\[挖鼻孔\]", "\[抓狂\]", "\[笑着哭\]", "\[无语\]", "\[捂脸\]", "\[喜欢\]", "\[笑哭\]", "\[疑惑\]", "\[赞\]", "\[眨眼\]"];
  var 表情列表 = "ÿ ÿ ÿ ÿ ÿ ÿ ÿ ÿ ÿ	 ÿú ÿ ÿ ÿþ ÿ ÿ ÿ ÿ ÿ ÿ ÿ ÿ ÿ ÿ ÿ ÿ ÿ ÿ ÿ ÿ ÿ ÿ ÿ  ÿ! ÿ\" ÿ# ÿ$ ÿ% ÿ& ÿ' ÿ( ";
  表情名 = 表情名列表.indexOf(表情名);
  if (表情名 < 0) {
    return false
  } else {
    return 表情列表.substr(5 * 表情名, 5)
  }
}

function 表情3查找(文本内容) {
  var 表情 = false;
  var 检索符号 = "\[";
  var 文本内容分割 = 文本内容.split(检索符号);
  if (文本内容分割.length > 1) {
    for (var i = 1; i < 文本内容分割.length; i++) {
      var s = 文本内容分割[i].search("\]");
      if (s < 4 && s > 0) {
        表情 = 表情3替换("\[" + 文本内容分割[i].substr(0, s + 1));
        if (表情) {
          文本内容分割[i] = 表情 + 文本内容分割[i].substr(s + 1);
        } else {
          文本内容分割[i] = 检索符号 + 文本内容分割[i];
        }
      } else {
        文本内容分割[i] = 检索符号 + 文本内容分割[i];
      }
    }
    文本内容 = 文本内容分割.join("");
  }
  return 文本内容
}```
