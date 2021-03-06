---
layout: post
title: "[Linux] 셔뱅(shebang) 사용법"
author: woong
categories: [Post, Linux]
toc: true
image: https://cdn.pixabay.com/photo/2017/04/27/01/31/question-2264166_1280.png
---

# 셔뱅(shebang)의 의미

운영체제 입장에서는 스크립트 파일이 

어떤 문법으로 짜여진건지 모른다.

(예: 이게 파이썬 코드야, 쉘 코드야?)

이걸 알려주기위해 스크립트 파일 첫줄에

```sh
#! /bin/bash
```
와 같이 인터프리팅 정보를 주는것을 셔뱅이라 한다.


## [위키피디아](https://ko.wikipedia.org/wiki/%EC%85%94%EB%B1%85) 설명

> 셔뱅(shebang)은 해시 기호와 느낌표(#!)로 이루어진 문자 시퀀스로, 스크립트의 맨 처음에 온다. 샤-뱅(sha-bang)[1][2][3], 해시뱅(hashbang)[4][5], 파운드-뱅(pound-bang)[2][6], 해시-플링(hash-pling)[2][7], 크런치뱅(crunchbang)이라고도 한다. 유닉스 계열 운영 체제에서 셔뱅이 있는 스크립트는 프로그램으로서 실행되며, 프로그램 로더가 스크립트의 첫 줄의 나머지 부분을 인터프리터 지시자(interpreter directive)로 구문 분석한다. 즉, 지정된 인터프리터 프로그램이 대신 실행되어 스크립트의 실행을 시도할 때 처음 사용되었던 경로를 인수로서 넘겨주게 된다.[8] 이를테면 스크립트의 경로가 path/to/script이고 다음의 줄로 시작한다면: `#!/bin/sh` 프로그램 로더는 프로그램 /bin/sh를 대신 실행하되 path/to/script를 첫 번째 인수로 넘겨준다. 셔뱅 줄은 일반적으로 인터프리터에 의해 무시되는데 그 까닭은 "#" 문자가 수많은 스크립트 언어에서 주석 표시자이기 때문이다. 스킴처럼 해시 마크를 주석 시작으로 사용하지 않는 일부 언어 인터프리터들은 목적에 맞게 셔뱅 줄을 무시하기도 한다. 다른 해결 방안으로는 전처리기에 의존하여 스크립트의 나머지 부분이 컴파일러나 인터프리터에 넘겨지기 전에 셔뱅 줄을 제거하거나 평가하게끔 하는 방법이다. 이를테면 여러 운영 체제에서 프리 파스칼로 작성된 프로그램을 실행할 수 있도록 하는 InstantFPC의 경우가 그러하다.[9] 

# 스크립트 파일 사용 예제


특정 스크립트 파일을 파이썬 코드로 작성하였다고 가정하자.

이때 아래와 같이 두 가지 스크립트 파일 실행이 가능하다.


## 1. 쌩으로 스크립트 파일 실행


```console
$>python script_file
```

이렇게 실행해도 되지만,

자주 사용하는 스크립트의 경우 아래가 훨~씬 편하다.


## 2. 셔뱅 + 파일 실행

```console
$>which python
/usr/bin/python
```

`which` 명령어로 python 경로를 알아낸후 스크립트 파일 첫줄에

```console
#! /usr/bin/python
```

추가 후 

```console
$>chmod +x script_file
```

로 실행 권한 부여 후

```console
$>./script_file
```

이렇게 `'쩜+슬러쉬+파일명'`으로 실행가능하다.
