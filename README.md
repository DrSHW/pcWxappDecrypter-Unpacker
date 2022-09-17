# PC小程序解密/逆向工具

### PC小程序解密

微信小程序在PC端是加密存储的，如果直接打开是看不到什么有用的信息的，需要经过解密才可以看到包内具体的内容。

若是手机端导入的`.wxapkg`包，无需此处的解密过程，可以直接进行源码逆向。

在这里使用Python程序`decrypt.py`进行解密，需要Python环境并安装解密模块：

```bash
pip install pycryptodome
```

配置完成后，找到PC小程序的`.wxapkg`文件位置，一般在微信目录下的`Applet`文件夹下，对应`Appid`的文件夹内。

执行：

```bash
python decrypt.py --wxid [小程序Appid] --file [.wxapkg文件路径] --output [解密后的文件存储路径]
```

示例：

```bash
python decrypt.py --wxid wx1234567890123456 --file D:\Demo\__APP__.wxapkg --output D:\Demo\decrypted.wxapkg
```

操作后即可得到解密后的文件，文件路径推荐使用绝对路径，`--file`等价于`-f`，`--output`等价于`-o`。

### 小程序逆向

这里借鉴了项目：https://github.com/yswunstoppable/wxappUnpacker 的源码。

先安装依赖：

```bash
npm install
```

配置完成后直接导入`.wxapkg`文件，即可在相同目录下生成逆向源码，执行：

```bash
node wuWxapkg.js [(解密后).wxapkg文件路径]
```

文件路径推荐使用绝对路径，示例：

```bash
node wuWxapkg.js D:\Demo\decrypted.wxapkg
```

即可在对应文件夹中生成对应小程序JS源码。
