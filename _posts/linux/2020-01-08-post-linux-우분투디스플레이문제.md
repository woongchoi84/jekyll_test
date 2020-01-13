---
layout: post
title: "[Linux] 우분투 관련 디스플레이 문제 해결방법"
author: woong
categories: [Linux]
toc: true
image: https://cdn.pixabay.com/photo/2015/01/08/18/24/children-593313_1280.jpg
---


# Ubuntu (Host)에서의 문제 해결

## gVIM 실행 시 E233(?) 에러

그래픽 드라이버 (nvidia) 재설치로 해결함

아래는 드라이버 설치 > gvim 설치 했을 때 에러가 나서

드라이버를 지우고 재설치하는 과정이다.

```console
$sudo apt --purge autoremove nvidia*
$sudo ubuntu-drivers autoinstall
```

---

  
# Window (Client)에서의 문제 해결

## SSH Display 문제

![](https://i.ibb.co/hg3Z6zJ/putty-Setupfor-Jupyter.png)

>위의 왼쪽 그림처럼 putty 설정

## 주피터 노트북 (or 랩) 환경 구성

해당 작업은 GitHub Setup 폴더에 추가해뒀다.

>위의 오른쪽 그림처럼 putty 설정

- Source port: 8888
- Destination: localhost:0.0

```console
$jupyter notebook --generate-config
$jupyter notebook password
```
