---
title: 关于如何解决协议版本过低的问题
author: certainstar
date: 2023-9-23
---

# 关于如何解决协议版本过低的问题
> 出现 `code 45` 并显示当前QQ版本过低，则说明当前使用的协议版本不满足最低协议版本，需要升级。

## 如何对协议版本进行升级
### 升级签名服务器的协议版本
- [x] 首先查看签名服务器的txlib文件夹中是否有升级到目标协议的文件夹(如果您是直接拷贝的本项目中的zip，则是没有68及以上版本的协议文件夹的)，如果想升级到68及以上版本，首先对目标协议文件夹进行下载，可以前往fuqiuluo大佬的签名服务器中的txlib文件夹中下载最新的协议版本，[下载地址](https://github.com/fuqiuluo/unidbg-fetch-qsign/tree/master/txlib)。
- [x] 假设想要升级到8.9.71版本，则需要下载8.9.71文件夹。下载完成后，对签名服务器中的 `start.bat` 文件即可。
进行修改。只用修改 `--library=txlib\8.9.63` 中的版本号即可，将版本号改为8.9.71，修改后的 `start.bat` 文件如下(已经输入过的android_id不用修改)：

```bat
bin\unidbg-fetch-qsign.bat --library=txlib\8.9.71 --port=8080  --count=1 --android_id=****...**** --host=0.0.0.0
```

- [x] 保存后，重启 `start.bat` 文件即可。

### 升级go-cqhttp中的协议版本
- [x] 进入go-cqhttp之前生成 `data` 文件夹，进入其中的 `version` 文件夹，创建一个名为 `6.json` 文件中，进入[大佬仓库](https://github.com/MrXiaoM/qsign/blob/mirai/txlib/)，在左侧找到对应协议文件夹并点击，找到该文件夹内的 `android_phone.json` 文件，复制该json文件内容，然后粘贴到 `6.json` 文件中，并将最后一行中的 `protocol-type` 的值改为6，修改后的 `6.json` 文件如下所示：

```json
{
    "apk_id": "com.tencent.mobileqq",
    "app_id": 537170072,
    "sub_app_id": 537170072,
    "app_key": "0S200MNJT807V3GE",
    "sort_version_name": "8.9.71.11735",
    "build_time": 1688560152,
    "apk_sign": "a6b745bf24a2c277527716f6f36eb68d",
    "sdk_version": "6.0.0.2551",
    "sso_version": 20,
    "misc_bitmap": 150470524,
    "main_sig_map": 16724722,
    "sub_sig_map": 66560,
    "dump_time": 1688560152,
    "qua": "V1_AND_SQ_8.9.71_4332_YYB_D",
    "protocol_type": 6
}
```

- [x] 保存后，重新启动 `go-cqhttp.bat` ，即可发现协议正在更新，然后重新处理滑条验证码，处理后会有类似以下提醒(可能会一直刷新该提醒，为正常情况)：

```cmd
[INFO]:Protocol -> connect to server *******
```

- [x] 再次重新启动 `go-cqhttp.bat` ，并且重新完成滑条验证码和短信验证码即可完成更新。

### 注意事项
***切记，在升级协议版本时，一定要保证签名服务器和go-cqhttp中的协议版本号一致，否则会出现异常问题***
