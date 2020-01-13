---
layout: post
title: "[Blog] Jekyll + github.io 블로그의 구글 검색 엔진 등록"
excerpt: "구글 서치 콘솔 사용법"
date: 2020-01-05
tags: [Post, Blog]
---


![](https://cdn.pixabay.com/photo/2015/02/02/15/28/bar-621033_1280.jpg)

# Google Search Console (구글 검색 콘솔)

>참조: [구글 서치 콘솔(구:웹마스터도구)사용법 가이드](https://www.twinword.co.kr/blog/search-console-guide/)

>참조: [구글 사이트 등록하기 (Google 검색노출)](https://imweb.me/faq?mode=view&category=29&category2=35&idx=15573)

위 두 링크에 있는 자료가 좋은것 같다.

내 Jekyll 블로그의 경우

- 속성 유형 선택 > URL 접두어 > https://woongchoi84.github.io/
- 소유권 확인 > 파일 업로드 (git push)
- sitemaps 에 sitemap.xml 추가 

순으로 해둔 상태이다.

사이트맵의 경우 

1. `Google Search Console` 페이지 좌측 메뉴의 sitemaps 클릭
2. 새 사이트맵 추가 > https://woongchoi84.github.io/sitemap.xml 제출

순으로 진행했다.

시간을 두고 좀 지켜봐야하는 것 같다.



# Google Custom Search Engine (구글 커스텀 검색 엔진)

[Minimal Mistakes 공식 블로그](https://mmistakes.github.io/minimal-mistakes/docs/configuration/#google-custom-search-engine)의 설명에 따르면

>Add a Google search box to your site.

이렇게 나온다.

내 블로그에 구글 서치 박스를 추가하는것 같은데

아직 해당 기능에 대한 확인 중이다.

