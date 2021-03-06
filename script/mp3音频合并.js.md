 # mp3音频合并.js
```
File=java.io.File;
FileOutputStream=java.io.FileOutputStream;
RandomAccessFile=java.io.RandomAccessFile;
var path=[];
path[0]="/sdcard/脚本/你好.mp3";
path[1]="/sdcard/脚本/我不好.mp3";
var pathe="/sdcard/脚本/合并后.mp3";
uniteAMRFile(path,pathe);

function uniteAMRFile(partsPaths, unitedFilePath) {
  //try {
    var unitedFile = new File(unitedFilePath+"2");
    var fos = new FileOutputStream(unitedFile);
    var ra = null;
    for (var i = 0; i < partsPaths.length; i++) {
      ra = new RandomAccessFile(partsPaths[i], "r");
      if (i != 0) {
        ra.seek(6);
      }
      var buffer = java.lang.String(new Array(1024 * 8+1).toString()).getBytes();
      var len = 0;
      while ((len = ra.read(buffer)) != -1) {
        fos.write(buffer, 0, len);
      }
    }
    ra.close();
    fos.close();
 // } catch (e) {}
}












```
