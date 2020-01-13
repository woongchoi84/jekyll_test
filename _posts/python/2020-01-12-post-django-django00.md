---
layout: post
title: "[Python] Django: Django로 홈페이지를 만들어보자 #1"
author: woong
categories: [Python]
toc: true
image: https://cdn.pixabay.com/photo/2014/05/07/15/19/django-339744_1280.png
---

# Django(장고) 설치 및 초기 설정

## django 설치 (WSL 기준, Ubuntu로 봐도 무방할듯)

```console
$>sudo pip3 install django 
```

의외로 시간이 좀 걸린다.


## 새 프로젝트 만들기

> main 이라는 프로젝트 생성 (이름은 정하기 나름!)

```console
$>django-admin startproject main
```

아래와 같은 Tree 구조의 폴더가 생성된다.

```console
├── main
│   ├── __init__.py
│   ├── asgi.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
└── manage.py
```

## App 생성

`manage.py` 가 있는 main 폴더에서 다음 명령어 실행

```console
$>python3 manage.py startapp timeline
```

`timeline`이라는 이름도 정하기 나름이다.

## 설정 파일 변경

> `main/main/setting.py` 수정

```python
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'timeline', # python3 manage.py startapp timeline 관련 해당 라인이 추가되었다.
]
...
LANGUAGE_CODE = 'ko' # 한국
TIME_ZONE = 'Asia/Seoul' # 서울, 서울, 서울 아름다운 이 거리...
USE_I18N = True
USE_L10N = True
USE_TZ = False # 한국 시간으로 하려면 False, True: UTC 시간
...
STATIC_ROOT = os.path.join(BASE_DIR, 'static') # 맨 아래에 해당 문구 추가
```

위와 같이 주석이 달린 부분을 수정하자!


## 모델 (timeline/model.py) 수정

```python
from django.db import models
from django.utils import timezone

class Post(models.Model):
	author = models.ForeignKey('auth.User', on_delete = models.CASCADE)
	title = models.CharField(max_length = 200)
	text = models.TextField()
	created_date = models.DateTimeField(default = timezone.now)
	
	def __str__(self):
		return self.title
```

## 모델이 변경되었음을 알리자

> Migration 실행

```console
$>python3 manage.py makemigrations timeline
$>python3 manage.py migrate
```

## 관리자 계정 추가

> `blog/admin.py` 파일 수정

```python
from django.contrib import admin
from.models import Post

admin.site.register(Post)
```

admin 계정 생성

```console
python3 manage.py createsuperuser
python3 manage.py runserver
```

`createsuperuser` 실행 시 

아이디/메일주소/비번을 입력한다.



## 관리자 계정으로 새로운 포스트 작성

> http://127.0.0.1:8000/admin 접속

접속해서 Post 메뉴에서 새로운 Post를 추가해본다.

![](https://i.ibb.co/2KJzXFw/001.png)

위 그림과 같이 현재 시각이 잘 맞는지 확인!



## 메인 페이지 접속 시 반응하도록 수정

> main/urls.py 수정

```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('timeline.urls')),
]
```

> timeline/urls.py 생성

```python
from django.urls import path
from . import views

urlpatterns = [
    path('',views.post_list,name='post_list'),
]
```

> timeline/views.py 수정

```python
from django.shortcuts import render
from django.utils import timezone
from .models import Post

def post_list(request):
    posts = Post.objects.filter(created_date__lte=timezone.now()).order_by('created_date')
    return render(request, 'timeline/post_list.html',{ 'posts':posts })
```

> timeline/templates/timeline/post_list.html 생성

[만들어둔 링크](https://github.com/woongchoi84/django/blob/master/blog/templates/blog/post_list.html)와 같이 수정

> [블루프린트 - 타임라인](https://github.com/codrops/Blueprint-VerticalTimeline) 가져오기

```console
cd timeline
mkdir static
cd static
git clone https://github.com/codrops/Blueprint-VerticalTimeline.git .
```

> 페이지 확인

```console
python3 manage.py runserver
```
http://127.0.0.1:8000/

접속해보면 아래와 같이 나오는 것을 확인 할 수 있다.


![](https://i.ibb.co/2nfxnkF/4.png)

---

> 참고: [장고(django) 시작하기 in 우분투](https://baejino.com/programing/django/how-to-start)
