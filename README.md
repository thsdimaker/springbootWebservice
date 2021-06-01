## 1)프로젝트 개요 및 환경

* OS
  
  개발Main : Windows 10
  
  Sub : WSL2(Ubuntu 18.0.4) - Linux 방식 배포 동시 연습
  
* jdk : 11.0.10
* Springboot : 2.4.6
* db : h2(1.4.200)


## 2) 각 단계별 목표
* 최대한 빠르게 CRUD 작성 및 Logic 이해


## 3) 개발 기한 및 상세 기록사항

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
1. JPA와 DB설정 및 동작 테스트 및 1차 빌드 배포 완료

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
  
 