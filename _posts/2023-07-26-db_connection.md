---
title: "DB Connection"
date: 2023-07-26 15:29:00 +0900
last_modified_at: 2023-07-26 15:29:00 +0900

categories:
  - database

tags: 
  - 데이터베이스
  - 커넥션 풀
  - db connection
  - db connection pool

toc: true
toc_sticky: true

header: 
  teaser: /assets/images/github-page.jpeg

sidebar:
  nav: "docs"
---
우리가 개발하는 웹 애플리케이션과 데이터베이스는 서로 다른 시스템이다. 

따라서 데이터베이스 드라이버를 사용하여 데이터베이스에 연결해야한다.

### 데이터베이스 연결의 생애주기

1. 데이터베이스 드라이버를 사용하여 데이터베이스 연결 열기
2. 데이터를 읽고 쓰기 위해 TCP 소켓 열기
3. TCP 소켓을 사용하여 데이터 통신
4. 데이터베이스 연결 닫기
5. TCP 소켓 닫기

위와 같이 데이터베이스 연결을 수립하고, 해제하는 과정은 비용이 많이 들어가는 작업이다.
