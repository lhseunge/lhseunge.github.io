---
title: "MarkDown 문법 정리"
date: 2023-00-00 00:00:00 +0900
last_modified_at: 2023-00-00 00:00:00 +0900

categories:
  - blog

tags: 
  - 마크다운
  - markdown
  - syntax

toc: true
toc_sticky: true

header: 
  teaser: /assets/images/github-page.jpeg

sidebar:
  nav: "docs"
---

## markdown syntax 
- 제목
```
# 제목1
## 제목 2
### 제목 3
#### 제목 4
##### 제목 5
###### 제목 6
```
# 제목1
## 제목 2
### 제목 3
#### 제목 4
##### 제목 5
###### 제목 6
---
- 줄바꿈  
```
띄어쓰기 2번  
또는 <br/>
```
띄어쓰기 2번  
또는 <br/>
---
- 수평선
```
---
***
```
---
***
---
- 글자 강조
```
**굵은 글씨**  
*이텔릭*  
_이탤릭_  
~~취소선~~  
<u>밑줄</u>  
ex)  
This is the **bold** text and this is the *italic* text and <u>let's</u> do ~~strikethrough~~
```
**굵은 글씨**  
*이텔릭*  
_이탤릭_  
~~취소선~~  
<u>밑줄</u>  
ex)  
This is the **bold** text and this is the *italic* text and <u>let's</u> do ~~strikethrough~~
---
- 인용문
```
> 인용문장
>> 중첩된 인용문
>>> 중첩된 인용문 2
```
> 인용문장
>> 중첩된 인용문
>>> 중첩된 인용문 2
---
- 목록
```
- 순서가 필요하지 않은 목록
    - 순서가 필요하지 않은 목록
        - 순서가 필요하지 않은 목록
* 순서가 필요하지 않은 목록
    * 순서가 필요하지 않은 목록
        * 순서가 필요하지 않은 목록
+ 순서가 필요하지 않은 목록
    + 순서가 필요하지 않은 목록
        + 순서가 필요하지 않은 목록

- 순서가 필요하지 않은 목록
    * 순서가 필요하지 않은 목록
    + 순서가 필요하지 않은 목록
```
- 순서가 필요하지 않은 목록
    - 순서가 필요하지 않은 목록
        - 순서가 필요하지 않은 목록
* 순서가 필요하지 않은 목록
    * 순서가 필요하지 않은 목록
        * 순서가 필요하지 않은 목록
+ 순서가 필요하지 않은 목록
    + 순서가 필요하지 않은 목록
        + 순서가 필요하지 않은 목록

- 순서가 필요하지 않은 목록
    * 순서가 필요하지 않은 목록
    + 순서가 필요하지 않은 목록
---
- 링크
```
[Title](link)
Click [here](https://lhseunge.github.io/) 
```
[Title](link)
Click [here](https://lhseunge.github.io/) 
---
- 이미지
```
![Image Description](https://lhseunge.github.io/assets/images/github-page.jpeg)
or
inline Image는 ![inline image](https://lhseunge.github.io/assets/images/github-page.jpeg "inline image") 이렇게 표시.
```
![Image Description](https://lhseunge.github.io/assets/images/github-page.jpeg)  
or   
inline Image는 ![inline image](https://lhseunge.github.io/assets/images/github-page.jpeg "inline image") 이렇게 표시.
---
- 표
```
| Header | value | Description |
| --: | :-- | :--: |
| 정렬 | --: | 우측정렬 |
| 정렬 | :-- | 좌측정렬 |
| 정렬 | :--: | 가운데정렬 |
```
| Header | value | Description |
| --: | :-- | :--: |
| 정렬 | --: | 우측정렬 |
| 정렬 | :-- | 좌측정렬 |
| 정렬 | :--: | 가운데정렬 |
---
- 코드
**inline code**
```
`해당 코드`는 강조할 부분 이다.
```
`해당 코드`는 강조할 부분 이다.
**block code**
```
 /``` <language>
 /```
```
html
 ```html
<div>text<div>
 ```
css
 ```css
div {
  font-size : 50px
}
 ```
javascript
 ```javascript
console.log("text")
 ```
java
 ```java
System.out.println("text");
 ```
sql
 ```sql
SELECT 'TEXT' FROM DUAL
 ```
python
 ```python
print("text")
 ```
plaintext
 ```plaintext
text
 ```
null
``` 
text
```
---
- 원시 HTML
```
<div>text<div>
```
<div>text<div>
 
