 # Base64(1).js
```
/**
     * �˱���Ϊ�����key��ÿ���ַ����±����Ӧ����������ı��롣
     */
    var enKey='ABCDEFGHIJKLmnopqrstuvwxyz01234abcdefghijklMNOPQRSTUVWXYZ+/56789';
    /**
     * �˱���Ϊ�����key����һ�����飬BASE64���ַ���ASCIIֵ���±꣬����Ӧ�ľ��Ǹ��ַ�������ı���ֵ��
     */
    var deKey=new Array(
        -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1,
        -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1,
        -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, 57, -1, -1, -1, 58,
        26, 27, 28, 29, 30, 59, 60, 61, 62, 63, -1, -1, -1, -1, -1, -1,
        -1,  0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 43, 44, 45,
        46, 47, 48, 49, 50, 51, 52, 53, 54, 55, 56, -1, -1, -1, -1, -1,
        -1, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 12, 13, 14,
        15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, -1, -1, -1, -1, -1
    );
    /**
     * ����
     */
    function encode(src){
        //��һ����������ű������ַ���Ч�ʱ����ַ�����Ӹߺܶࡣ
        var str=new Array();
        var ch1, ch2, ch3;
        var pos=0;
       //ÿ�����ַ����б��롣
        while(pos+3<=src.length){
            ch1=src.charCodeAt(pos++);
            ch2=src.charCodeAt(pos++);
            ch3=src.charCodeAt(pos++);
            str.push(this.enKey.charAt(ch1>>2), this.enKey.charAt(((ch1<<4)+(ch2>>4))&0x3f));
            str.push(this.enKey.charAt(((ch2<<2)+(ch3>>6))&0x3f), this.enKey.charAt(ch3&0x3f));
        }
        //��ʣ�µ��ַ����б��롣
        if(pos<src.length){
            ch1=src.charCodeAt(pos++);
            str.push(this.enKey.charAt(ch1>>2));
            if(pos<src.length){
                ch2=src.charCodeAt(pos);
                str.push(this.enKey.charAt(((ch1<<4)+(ch2>>4))&0x3f));
                str.push(this.enKey.charAt(ch2<<2&0x3f), '=');
            }else{
                str.push(this.enKey.charAt(ch1<<4&0x3f), '==');
            }
        }
       //��ϸ��������ַ�������һ���ַ�����
        return str.join('');
    }
    /**
     * ���롣
     */
    function decode(src){
        //��һ����������Ž������ַ���
        var str=new Array();
        var ch1, ch2, ch3, ch4;
        var pos=0;
       //���˷Ƿ��ַ�����ȥ��'='��
        src=src.replace(/[^A-Za-z0-9\+\/]/g, '');
        //decode the source string in partition of per four characters.
        while(pos+4<=src.length){
            ch1=this.deKey[src.charCodeAt(pos++)];
            ch2=this.deKey[src.charCodeAt(pos++)];
            ch3=this.deKey[src.charCodeAt(pos++)];
            ch4=this.deKey[src.charCodeAt(pos++)];
            str.push(String.fromCharCode(
                (ch1<<2&0xff)+(ch2>>4), (ch2<<4&0xff)+(ch3>>2), (ch3<<6&0xff)+ch4));
        }
        //��ʣ�µ��ַ����н��롣
        if(pos+1<src.length){
            ch1=this.deKey[src.charCodeAt(pos++)];
            ch2=this.deKey[src.charCodeAt(pos++)];
            if(pos<src.length){
                ch3=this.deKey[src.charCodeAt(pos)];
                str.push(String.fromCharCode((ch1<<2&0xff)+(ch2>>4), (ch2<<4&0xff)+(ch3>>2)));
            }else{
                str.push(String.fromCharCode((ch1<<2&0xff)+(ch2>>4)));
            }
        }
       //��ϸ��������ַ�������һ���ַ�����
        return str.join('');
    }```
