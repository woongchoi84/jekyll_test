---
layout: post
title: "[Linux] Bash Shell 기반 리눅스에서 폴더 이동할 때마다 내용 리스트업하기"
author: woong
categories: [Linux]
toc: true
image: https://cdn.pixabay.com/photo/2015/01/08/18/24/programming-593312_1280.jpg
---

# .bashrc 파일 수정

## 아래 문구 추가

```console
function	cd	{ if (( $#==0 )); then builtin cd ~ && ls; else builtin cd "$@" && ls; fi }
cd		.
```

함수를 해석해보자면,

> 뒤에 `cd`와 함께 쓰이는 인자(argument)의 갯수가 0이면,

(즉 `cd`만 쓰면)

유저의 `home`폴더로 이동하고,

> 인자의 갯수가 0이 아니면

뒤에 오는 첫번째 인자로 이동한다.

그다음 `ls` 커맨드로 현재 폴더의 내용을 화면에 리스트업 해준다.

## bash의 파라미터 처리

- $#: 			the number of arguments, not counting $0
- $@: 			all positional parameters except $0
- $*: 			all positional parameters except $0
- $0: 			the first positional parameter, equivalent to argv[0] in C
- $1 ... $9: 	the argument list elements from 1 to 9


## xxxrc 파일이란?

- "runtime configuration"
- "run control"
- "run commands"

요정도의 의미로 해당 프로그램의 환경설정 파일이라고 생각하자.
