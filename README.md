## 1)프로젝트 개요 및 환경


* jdk : 11
* Springboot : 2.4.6
* db : h2(1.4.200)


## 2) 각 단계별 목표
* 최대한 빠르게 CRUD 작성 및 Logic 이해


## 3) 개발 시작
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

```
Problem)
H2 데이터베이스 실행 오류.(Windows 환경에서 아에 열리지 않음)

Solution)
(2-3시간 소모)
JDK 1.8x 버전 지우면서 자바 컴파일러 까지 같이 지움.
결국 java가 인식이 안됬어서, h2-database 마찬가지로 실행이 안됨.
``` 
  
 