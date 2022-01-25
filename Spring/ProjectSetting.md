# Create a project

[www.start.spring.io](http://www.start.spring.io) 로 스프링 boot 기본 설정 가능

### ■ Gradle  vs Maven

| Maven | Gradle |
|-----|------|
| 내가 사용할 라이브러리가 작동하는데 필요한 다른 라이브러리까지 관리하여 네트워크를 통해 자동으로 다운 받아준다.(XML로 라이브러리 정의)| 빌드 배포 툴이다. Ant역할과 배포 스크립트의 기능을 모두 사용가능하다.(별도의 스크립트를 통해 라이브러리 정의 -> 간결) |

<u><b>요약 : Gradle이 Maven 보다 빨라 요즘 많은 개발자들이 선호한다.</b></u>

Gradle 사용하자..


Dependencies   = 라이브러리 함께할것들

 - Spring Web , Thymeleaf

 main 과 test가 있음 <u>테스트 코드 ★</u>

build.gradle 안에 아까 설정한 것들 전부다 있음

### 라이브러리 살펴보기

Gradle이 의존성 있는 라이브러리를 관리함 (만약 이 라이브러리에 필요한 다른 라이브러리를 다운받아줌)
<br>

#### 스리링 부트 라이브러리

- bspring-boot-starter-web
    - spring-boot-starter-tomcat:톰캣(웹서버)
    - spring-webmvc : 스프링 웹 MVC
- spring-boot-starter-thymeleaf : 타임리프 템플릿 엔진(View)
- spring-boot-starter(공통) : 스프링 부트 + 스프링 코어 + 로깅
   - spring-boot
     -  spring core
   - spring-boot-starter-logging
     - logback, slf4j

#### 테스트 라이브러리

- spring-boot-starter-test
   - junit : 테스트 프레임워크
   - mockito : 목 라이브러리
   - assertj : 테스트 코드를 좀 더 편하게 작성하게 도와주는 라이브러리
   - spring-test : 스프링 통합 테스트 지원
 