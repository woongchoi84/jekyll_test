---
layout: post
title: "[Python] Window-Sub-System for Linux (WSL)에서 파이썬(Python) 기반 파이어폭스(Firefox) 웹 크롤링(crawling)"
author: woong
categories: [Python]
toc: true
image: https://cdn.pixabay.com/photo/2017/07/25/22/54/office-2539844_1280.jpg
---

# WSL + 최신 버전 FireFox 에서 문제일으킴

2020년 1월 기준 WSL 기반 개발환경에는,

최신 버전의 파이어폭스 (FireFox)가 문제를 일으키는듯하다.

파이어 폭스 7x 버전에서 69.0 버전으로 다운그레이드 하자.

```bash
#! /bin/bash
# ==================================================
#  firefox downgrade
# ==================================================
# [Make Backup File]
wget -O ~/firefox.tar.bz2 "https://ftp.mozilla.org/pub/firefox/releases/69.0/linux-x86_64/en-US/firefox-69.0.tar.bz2"
sudo tar xjf ~/firefox.tar.bz2 -C /opt/
sudo mv /usr/lib/firefox/firefox /usr/lib/firefox/firefox_bug
sudo ln -s /opt/firefox/firefox /usr/lib/firefox/firefox
rm ~/firefox.tar.bz2

# [Completed Message]
echo "=================================================="
echo " firefox (69.0) has been installed"
echo "=================================================="
```

위와 같이 shell script 작성 후

실행시키면 WSL에 설치된 파이어폭스가 69.0 버전으로 바뀐다.

나같은 경우는 `bug_fix.sh`이란 파일을 만들어 위 코드를 넣어 저장하고

```console
chmod +x bug_fix.sh
```

리눅스 명령어를 통해 실행권한을 부여 후

```console
./bug_fix.sh
```

터미널에서 위 명령어를 통해 문제를 해결하였다.

(2020년 1월 4일 기준)

---

![](https://cdn.pixabay.com/photo/2016/10/27/10/37/arrow-1773951_1280.png)

WSL에서는 크롬브라우저(Chrome) 설치에 실패해서

아래 예제와 같이 selenium + FireFox Web Driver를 통해

파이썬 크롤링이 가능하다.

[WSL 웹크롤링](https://github.com/woongchoi84/project/blob/master/python/webCrawler/00_test.ipynb)

자세한 내용은 위 WSL 웹크롤링 링크 참조!!!


빠른 시일내로 마이크로소프트(Microsoft)에서 WSL2를

릴리즈하길 바란다.

이상!
