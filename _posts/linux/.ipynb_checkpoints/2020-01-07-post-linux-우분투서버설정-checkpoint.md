---
layout: post
title: "[Linux] 우분투 18.04 LTS 데스크탑 설정"
last_modified_at: 2020-01-07
categories:
  - Post
tags:
  - Post
  - Linux
toc: true
toc_label: "설정해야하는 목록"
toc_icon: "list"
---

![](https://cdn.pixabay.com/photo/2013/07/12/14/08/keyboard-147827_1280.png)

# 기본 세팅(WSL, Ubuntu 공통)

## Git 설치 및 autosetup 스크립트 clone

```console
$sudo apt-get update
$sudo apt-get install git
$git clone https://github.com/woongchoi84/setup
```

## 개발환경에 맞는 ./autosetup.bsh 실행

- jekyllSetup: 블로그용 지킬 설치
- wslSetup: WSL기반 TensorFlow, Python 개발 환경
- ubuntuSetup: 우분투 서버
- jupyterSetup: 주피터 노트북 환경설정

> 아래는 실행 예

```console
$./autosetup.bsh
```

## 레포지토리 문제 발생 시

### 레포지토리는 그냥 오리지널 버전으로

다음 카카오 레포지토리 주소가 또 바뀌었다...

속도 차이 얼마 안나니 그냥 오리지널 버전 쓰는게 편한것 같다.


# 우분투 서버 (w/ GPU)

## 드라이버 설치

```console
$sudo ubuntu-drivers autoinstall
```

>드라이버 설치 전 발생했던 문제들

- 사용자 계정 로그인 화면에서 엄청나게 버벅거림
- 시도때도 없는 멈춤현상
- GVIM 디스플레이 문제

## 추가사항

### 드라이버 설치 후 autosetup을 하면 우분투가 많이 아프다.

(gvim 같은 것 실행하면 display error 뿌린다)

기본 설정 (tensorflow, jekyll 등) 설치 후 드라이버 설정 잡는게 좋겠다.

![](https://cdn.pixabay.com/photo/2012/04/15/17/55/note-34687_1280.png)
{:.some-css-class style="width: 200px"}

## 기억해야할 것들

### 설치는 영문버전으로

이래야 디버깅할때 구글링이 가능하다.


![](https://cdn.pixabay.com/photo/2017/02/18/11/00/checklist-2077020_1280.jpg)
{:.some-css-class style="width: 200px"}


## 추가로 해야할 사항들...

### SSH Display 문제 해결

쉬운게 없다. 따로 포스팅해야겠다.

Putty 카테고리의 `Connection -> SSH -> X11`에서

- X11 forwarding의 Enable X11 forwarding 체크박스 체크!
- x display location에 localhost:0.0 기입

### 주피터 노트북 (or 랩) 환경 구성

집에서도 접속이 가능할지는 모르겠다.

### 파이어폭스 최신버전에서 크롤링 가능여부 확인

WSL 환경에서는 최신버전의 파이어폭스가 문제였는데 

아마 우분투에서는 괜찮을듯

