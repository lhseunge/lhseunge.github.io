---
title: "[Java] 접근 제한자"
date: 2022-11-13 23:46:00 +0900
last_modified_at: 2022-11-13 23:46:00 +0900

toc: true
toc_sticky: true

header: 
  teaser: /assets/images/github-page.jpeg

categories:
  - java

tags: 
  - java
  - 접근 제한자
  - 접근 제어자

sidebar:
  nav: "docs"
---
# 접근 제한자 

## 접근 제한자란?
접근 제한자(Access Modifier)는 클래스 및 인터페이스, 그리고 이들이 가지고 있는 멤버의 접근을 제한하기 위해 사용. 


## 접근 제한자의 종류

|접근 제한자|적용 대상|접근 범위|
|----------|---------|---------------------|
|public|클래스, 필드, 생성자, 메소드|모든 클래스에서 접근 가능|
|protected|필드, 생성자, 메소드|상속 받은 클래스이거나, 같은 패키지 내부의 클래스|
|(default)|클래스, 필드, 생성자, 메소드|같은 패키지 내부의 클래스|
|private|필드, 생성자, 메소드|모든 클래스에서 접근 불가능|
