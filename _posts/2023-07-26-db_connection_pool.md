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
DBCP에 대해 보기 전, DB Connection을 알 필요가 있음 [__🔗DB Connection__](https://lhseunge.github.io/database/db_connection/)이란?  

## DB Connection Pool
 
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

일례로 반복문을 통해서 10번의 DB Access를 수행한다면?

조건

1. 단일 Thread 환경
2. 병렬처리 사용하지 않음

```java
10번 반복 수행 
    회원Id로 회원 정보 조회
```

위 의사코드를 수행했을 때,

1개의 Thread가 10번의 DB Access를 하게됨

→ Connection Pool 에서 Connection 대여 - 반환을 10회 수행하게 됨 

→ 반복을 수행하더라도 Connection Pool안의 Connection 사용량은 변하지 않음

- 1개 Thead, 1개 Connection만 사용한다고 Thread 수와 Connection pool 크기를 같게 설정하면 안됨
- Connection을 반환하고, 새로운 Connection을 대여받는 동안 기존 Connection이 반환되지 않는 상황이 발생할 수 있고 대기 상태를 유발할 수 있음.
- 그러나 모든 요청이 DB Access를 요구하지 않을 수 있기 때문에 **성능 테스트를 거친 후 조정이 필요함**

**너무 큰 크기의 DBCP는 지속적인 DB 서버 리소스를 소모하고,**  

**너무 적은 크기의 DBCP는 대기 상태를 유발함**  

  

병렬처리로 DB Access를 하게 된다면? 

→ 작업을 수행하는 Thread만큼 Connection을 대여하게된다. 

→ Connection Pool의 Connection 이상으로 DB Access 요청이 발생한다면, Connction Pool은 대기 상태로 이어지고 애플리케이션 성능에 영향을 끼친다.

### 동시 접속자가 많으면?

→ 남아있는 Connection이 없을 때

대기 상태 (Waiting State)

Connection Pool에 빈 Connection이 없는 경우, 새로운 접속자는 대기 상태에 들어가게됨 

이러한 상태에서 접속자는 다른 접속자가 Connection을 반환하길 기다리고, 

대기 상태가 길어질 경우, 애플리케이션의 응답 시간이 지연되거나 사용자 경험이 저하될 수 있음

[__🔗마법의 공식 from 우테크 블로그__](https://techblog.woowahan.com/2664/)

pool size =  Tn * (Cm - 1) + 1

- Tn = 전체 Thread 개수
- Cm = 하나의 Task에 동시에 필요한 Connection 수
