 # 音乐🎶.js
```
"ui";

//音乐文件的后缀名
var musicExts = [".mp3", ".wma", ".rm", ".wav", ".mid", ".ape", ".flac"];
//扫描路径
var path = files.getSdcardPath();
//保存音乐文件列表的数组
var musicFiles = [];

var number=0;

ui.layout(
    <vertical  bg="#ffffff">
        <list id="files" layout_weight="1">
            <linear bg="?selectableItemBackground">
                <text id="number" gravity="center" textSize="25sp" text="{{this.number}}" bg="#ff5722" w="50" h="70" margin="16" />
                <vertical>
                    <text id="name" textSize="16sp" textColor="#000000" text="{{this.name}}" marginTop="16" maxLines="1" ellipsize="end"/>
                    <text id="path" textSize="13sp" textColor="#929292" text="{{this.path}}" marginTop="8" maxLines="1" ellipsize="end"/>
                </vertical>
            </linear>
        </list>
        <progressbar id="progressbar" indeterminate="true" style="@style/Base.Widget.AppCompat.ProgressBar.Horizontal"/>
    </vertical>
);

ui.files.setDataSource(musicFiles);

ui.files.on("item_click", function(item, pos) {
    media.playMusic(item.path, 1);
});

//启动线程来扫描音乐文件
threads.start(function() {
    listMuiscFiles(path, musicFiles);
    ui.run(() => {
        ui.progressbar.setVisility(8);
    });
});

function listMuiscFiles(dir, list) {
    //遍历该文件夹的文件
    files.listDir(dir).forEach(fileName => {
        var path = files.join(dir, fileName);
        //如果是子文件夹则继续扫描子文件夹的文件
        if (files.isDir(path)) {
            listMuiscFiles(path, list);
            return;
        }
        for (var i = 0; i < musicExts.length; i++) {
            //如果文件名的后缀是音乐格式
            if (fileName.endsWith(musicExts[i])) {
                //则把它添加到列表中
                number++;
                list.push({
                    number:number,
                    name: fileName,
                    path: path
                });
            }
        }
    });
}```
