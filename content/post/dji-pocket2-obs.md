---
title: "DJI Pocket2の映像をRTMP経由でOBSから受信する"
description: "DJI Pocket2の映像をRTMP経由でOBSから受信する"
date: "2024-03-01T18:42:56+09:00"
thumbnail: ""
categories:
  - "blog"
tags:
  - "tech"
---

DJI Pocket2 の映像を OBS に取り込む方法を探していたところ、push なデバイスから RTMP 経由で取れる例がありました。  
参考元: https://do-gugan.com/blog/archives/2021/08/rtmp.html

2024/3 月現在でも動作したことを確認したので、メモを残しておきます。

<!--more-->

参考元と同じように、nginx の docker イメージを立てて見ます。

```bash
docker run -d -p 1935:1935 --name nginx-rtmp tiangolo/nginx-rtmp
```

nginx.conf も同様に次のように設定します。

```nginx
worker_processes auto;
rtmp_auto_push on;
events {}
rtmp {
    server {
        listen 1935;
        listen [::]:1935 ipv6only=on;

        application live {
            live on;
            record off;
            push rtmp://127.0.0.1/streamout;
        }
        application streamout {
            live on;
            record off;
        }
    }
}
```

遅延を LAN 内で検証してみました。
遅延は、送信側: 画質 1080p,配信品質: HD で約 4 秒程度でした。
![遅延確認](/medicine-t/images/dji-pocket2-obs/image.png)

配信品質をスムーズにすると、遅延が 2 秒程度になりました。
![遅延確認2](/medicine-t/images/dji-pocket2-obs/image2.png)

思ったより使えそうな感じですね。720p とか画質を下げればもう少し遅延が減るかもしれないですね。
LAN がある構内で配信するとかなら耐えられるかも？

あと、docker で用意できるってのは気楽でいいですね。
NodeCG とかを立ててる PC でこれも立てておくとか、いいかもしれません。

DJI Pocket2 本体は割りと発熱していたので、電池持ちが心配なのと、夏場は熱停止も気になりますところですね。

以上です。
