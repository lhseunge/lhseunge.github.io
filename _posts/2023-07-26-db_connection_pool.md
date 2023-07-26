---
title: "DB Connection Pool(DBCP)"
date: 2023-07-26 15:30:00 +0900
last_modified_at: 2023-07-26 15:30:00 +0900

categories:
  - database

tags: 
  - 데이터베이스
  - 커넥션 풀
  - db connection pool
  - db access

toc: true
toc_sticky: true

header: 
  teaser: /assets/images/github-page.jpeg

sidebar:
  nav: "docs"
---
[__🔗DB Connection__](https://lhseunge.github.io/database/db_connection/)이란?

수 많은 사용자가 서버에 요청을 보냈을 때 그만큼 Connection을 생성하게 되면 서버에 과부하가 걸리게 된다. 

DBCP는 이러한 상황을 예방하기 위해 애플리케이션이 실행 될 때 미리 정의된 수만큼 DB Connection을 생성하고, DB작업이 필요할 때 생성해둔 Connection을 “대여”받아 재사용한다. 

작업을 마친 Connection은 Connection Pool로 반환되고, 작업을 수행하지 않는 Connection은 유휴 상태로 전환되어 Connection Pool 크기를 유지하여 DB 성능을 최적화 한다.

### 요약

1. 애플리케이션 실행 시 정의된 수만큼 DB Connection **생성**
2. DB 작업이 필요할 때 생성해둔 Connection을 **대여**받아 재사용
3. 작업을 마친 Connection은 Connection Pool로 **반환**
4. 작업을 수행하지 않는 Connection은 **유휴상태**로 전환

### DBCP와 DB Access의 상관 관계

DB Access (데이터베이스 접근 or 연결)

DB에 접속하고, 데이터를 읽거나 쓰는 프로세스 

→ DB에 접근하여 데이터를 조회, 수정, 삭제 하는 행위를 의미

### 동시 접속자가 많으면?

→ 남아있는 Connection이 없을 때

대기 상태 (Waiting State)

Connection Pool에 빈 Connection이 없는 경우, 새로운 접속자는 대기 상태에 들어가게됨 

이러한 상태에서 접속자는 다른 접속자가 Connection을 반환하길 기다리고, 

대기 상태가 길어질 경우, 애플리케이션의 응답 시간이 지연되거나 사용자 경험이 저하될 수 있음

### WAS 쓰레드와 커넥션 풀 수의 관계

가장 좋은 방법은 애플리케이션을 실제 운영할 시스템 환경에서 성능 테스트를 진행하는 것

성능 테스트를 진행하면서 지금까지 살펴본 DBCP에 대한 원리와 설정을 위한 값들을 복기하면서 시스템 환경에 최적화된 값을 찾아 내는 것이 좋다

실제 운영중인 서비스에서 DBCP 값이 200에 가까운 수치가 설정되어 있어, 문제가 발생된 경우를 보았다. 무엇보다, WAS Thread 수는 DB Connection Pool의 갯수보다 더 적게 설정 되어 있었는데, 이러한 점을 효율적이지 못하다.

그렇다면, WAS의 Thread의 개수가 DB의 Connection Pool의 갯수 보다 많아야 하는 이유는 무엇일까? 

그 이유는 애플리케이션에 대한 모든 요청이 DB에 접근하는 것은 아니기 때문이다.

**WAS의 Thread는 Connection Pool의 갯수보다 여유있게 설정하는 것이 좋다.**

Connection Pool은 시스템의 환경에 따라 다르지만 보통 40~50개로 지정하면 Thread는 이보다 +10개 정도 더 지정하는 것이 바람직하다. 

하지만 최적의 성능의 위해서는 실제 요청이 얼마나 들어오는지 파악하는게 중요하며 가장 좋은 방법은 앞서 말한것 처럼 성능 테스트를 통해 최적화된 값을 구하는 것이다.  

[__🔗마법의 공식 from 우테크 블로그__](https://techblog.woowahan.com/2664/)

pool size =  Tn * (Cm - 1) + 1

- Tn = 전체 Thread 개수
- Cm = 하나의 Task에 동시에 필요한 Connection 수
