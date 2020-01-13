---
layout: post
title: "[Linux] CentOS: Xlib extension RANDR mission on display"
author: woong
categories: [Linux]
toc: true
image: https://cdn.pixabay.com/photo/2015/01/08/18/24/children-593313_1280.jpg
---

# Xlib: extension "RANDR" missing on display 에러

putty + Xming 조합으로 해결하였다.

### Host $DISPLAY

```console
$echo $DISPLAY
localhost:10.0
```

터미널에서 DISPLAY 환경변수를 확인해보면

`localhost:10.0` 이다

xming 트레이아이콘에 마우스를 올려보면

아래와 같다.

![](https://i.ibb.co/dGVRmWs/xmingtray.png)

### 이유는 모르겠지만 putty는 xming에 맞추자!

그냥 putty설정에서

![](https://i.ibb.co/CnLNMN1/centos-Putty.png)

localhost:0.0으로 잡아주고 실행하면

에러 메시지가 사라진다.

`/etc/ssh/ssh_config'의 

X11 Forward 옵션은 건드리지 않았다.


---
