# 실행결과(최종완성)

![Main_Page](https://user-images.githubusercontent.com/59603054/120926322-55a53e00-c717-11eb-9105-70149c33c0bf.jpg)

[클릭! 상세페이지 구현 확인 링크](https://github.com/thsdimaker/springbootWebservice/issues/1)

## 1)프로젝트 환경 및 개요

**-1) <u>프로젝트 환경</u>**
* OS
  
  개발Main : Windows 10
  
  Sub : WSL2(Ubuntu 18.0.4) - Linux 방식 배포 동시 연습


* Springboot : 2.4.6

  
* JDK : 11.0.10


* Db : h2(1.4.200)
  

* Css

<ol>1. Bootstrap</ol>
<ol>2. jumbotron-narrow</ol>

* Dependencies
```
1. 내장WAS
2. H2 database
3. Spring Data JPA
4. Thymeleaf
5. lombok
6. Validation
```
  



**-2) <u>프로젝트 개요</u>**

Spring MVC를 활용한 CRUD

## 2) 각 단계별 목표
* 전체 : Rest API 개발 및 게시판 CRUD
* 상세
```
-1. 프로젝트 환경설정
-2. 도메인 분석 설계
-3. 애플리케이션 구현 준비
-4. 회원 도메인 개발
-5. 상품 도메인 개발
-6. 주문 도메인 개발
-7. 웹 계층 개발
```


## 3) 개발 기한 및 상세 기록사항

* 2021.06.10

```
1. 정상 작동하는 테스트 사진 혹은 GIF 파일 Github Issue란에
올린 후 링크 걸기
```

* 2021.06.08

```
1. 전체 완성 및 문서작성 시작.
2. 추후 재복기 예정
```



* 2021.06.06

```
[ 완 성 ]
1. 상품 주문
2. 주문 목록 검색, 취소
```

* 2021.06.05

```
1. 웹 계층 개발
ㄴ>1) 상품 등록
ㄴ>2) 상품 목록
ㄴ>3) 상품 수정
```


* 2021.06.03

```
1. 06.02 미완성 목록들 추가 개발 
2. 웹 계층 개발 시작
ㄴ> 회원 등록, 조회 완성

```


* 2021.06.02
```
1. 주문 도메인 개발
ㄴ> 주문, 주문상품 엔티티(ㅇ)
ㄴ> 주문 리포지토리(ㅇ)
ㄴ> 주문 서비스(x)
ㄴ> 주문 기능 테스트(x)
ㄴ> 주문 검색 기능(x)
```


* 2021.06.01
```
1. 상품 도메인 개발
2. 상품 서비스 개발

```

* 2021.05.31

```
1. 각 항목별 테이블 설정 세팅 완료

2. 회원 도메인 개발
-1) 회원 리포지토리 개발
-2) 회원 서비스 개발
-3) 회원 기능 테스트
```

* 2021.05.30
```
1. JPA와 DB설정 및 동작 테스트 및 1차 빌드 배포 테스트 완료
```



* 2021.05.29

```
1. JDK 설치 및 프로젝트 Preference 설정
2. 기초 Dependencies 설정
-1)내장WAS(MVC)
-2)Lombok
-3)Thymeleaf
-4)h2(Database)
-5)JPA
3. 각 라이브러리 성능 테스트
ex) HelloController, H2 db 성능테스트
```

## 4) 문제점 발생

* 2021.06.02
```
Problem)
(Db연결이 꺼진상태)
org.h2.jdbc.JdbcSQLNonTransientConnectionException: Connection is broken: "java.net.SocketTimeoutException: connect timed out: localhost" [90067-199]

Solution)
그냥 단순 연동

How?)
H2가 메모리 방식이 아니라, 설치형 방식을 택했기 때문에, 항상 켜져있는걸로
생각했었음. 
```

* 2021.05.30

```
Problem)
(Db테이블 생성 오류)
org.h2.jdbc.JdbcSQLInvalidAuthorizationSpecException: Wrong user name or password [28000-200]
org.hibernate.service.spi.ServiceException: Unable to create requested service [org.hibernate.engine.jdbc.env.spi.JdbcEnvironment]

Solution)
yml 띄어쓰기 문제 해결

How?) @id 어노테이션 javax.persistence 로 제대로 임폴트 되었는지 확인 - > jpa External libraries 확인
- > Junit Dependencies 확인 - > junit4 정확히 임폴트 확인 - > 불필요한 junit5 path 설정 되어 있는 의존성 삭제 - >
 추후 오류 지속 - >Hibernate 오류 확인 - > application.yml 쪽 문제 있는 것 확인 - > 검색 후 띄어쓰기 문제 확인
```


```
Problem)

상황 : Junit4로 테스트 중 Db연동 커넥션이 이루어지지 않음.

Database "C:/Users/ ~" not found, 
either pre-create it or allow remote database creation 
(not recommended in secure environments) [90149-200] 



Solution)
(1시간 소모)
이전에 진행했던 스프링 부트 프로젝트에서 같은 8082포트를 사용했기에
[cmd]창 상황에서 8082 포트를 죽이고 다시 재설정

How?)

Junit 버전 확인(External Libraries) - >  import 된 Assertion 확인 - > 
아무 이상 X - > Db 자체 이상이 있는것 확인 - > 포트 확인 - > h2 자체 8082 포트 사용하는 것 확인
- > 8082가 계속해서 사용중이라 이전것 불러오는 상태 - > 8082 포트 죽임 - > 성공

```


* 2021.05.29
```
Problem)
H2 데이터베이스 실행 오류.(Windows 환경에서 아에 열리지 않음)

Solution)
(2-3시간 소모)
JDK 1.8x 버전 지우면서 자바 컴파일러 및 Kit까지 같이 지움.
결국 java가 인식이 안됬어서, h2-database 마찬가지로 실행이 안됨.

How?)
1. H2-console 계속해서 재설치 및 재부팅 - > Sprign Boot 버전 변경 확인 - > 공식 문서 확인
- > H2-console 또한 jre가 필요하다는 점 확인 - > [cmd] 연 후 java 버전 확인 - > 인식X
- > 환경 변수 재설정 - > 그래도 오류 - > 다시 재설치 - > 성공  

학습)
- > 너무 당연하지만, 무언가 지울 때는 신중히 지워야 함.
``` 
  
 
