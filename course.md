# 自定义背景详细教程

1. 先安装nodejs（如果已经正确安装并添加到环境变量的跳过这一步）
   
   详细教程：[点我查看](https://blog.csdn.net/Small_Yogurt/article/details/104968169)

2. 在一个自己能找到的目录下放入自定义的背景图片，重命名为`image.png`

3. 在同一目录下新建一个文本文档，双击打开，里面写入以下内容：

```js
var http=require('http');
var fs=require('fs');
var root="./image.png" //你本地图片路径
var server=http.createServer(function(req,res){
    fs.readFile(root+req.url,function(err,data){
        res.writeHeader(200,{'content-type' : 'html;charset="utf-8"'});
        res.write(data);
        res.end();
    })
}).listen(23333);
console.log('服务器开启成功');
```

4. 保存文件并关闭编辑器，然后将文件名改为`index.js`

5. 在当前文件夹（指index.js文件所在的文件夹）下打开cmd，输入`node index.js`

6. 如果看到**服务器开启成功**的字样，表示已经成功启动本地服务器了，重启洛雪就可以看到自己的背景图片了