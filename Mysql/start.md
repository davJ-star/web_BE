첫 글이다.


# mysql과 백엔드 연동
## root로 만드는데 에러가 생겨서 jsw 계정을 만들었다. (mysql shell)
[참고]()

----


## 존재하는 (만든) 계정, 이를 연결한다.
_데이터 소스 구성_ 과 _하이버네이트 구성_ 을 필수로 넣는편이다.(편한것도 있고..)


### [application.properties(yml)](https://velog.io/@alswl689/MySQL-JPA-SpringBoot-%EC%97%B0%EB%8F%99-%EB%B0%8F-%ED%85%8C%EC%8A%A4%ED%8A%B8Gradle) 또는 [MySQL 연동하기 with JPA](https://mroh1226.tistory.com/201)
```properties
# 스프링 애플리케이션 이름
spring.application.name=api-server

# _데이터 소스 구성_
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
# _데이터베이스 URL_ 및 타임존 설정
# mysql://[DB URL]:[port]/[DB Name]?serverTimezone=UTC
spring.datasource.url=jdbc:mysql://localhost:3306/homebar_db?serverTimezone=Asia/Seoul
# _데이터베이스 사용자 이름_
spring.datasource.username=root
# _데이터베이스 비밀번호_
spring.datasource.password=9999

## 만약에 선택에 따라 h2-console에 대해 넣을 수도 있다.


# _하이버네이트 구성_
# 콘솔에 SQL 쿼리 표시
spring.jpa.properties.hibernate.show_sql=true
# SQL 쿼리를 보기 쉽게 형식화
spring.jpa.properties.hibernate.format_sql=true
# _엔티티 클래스를 기반으로 데이터베이스 스키마 자동 업데이트_
spring.jpa.hibernate.ddl-auto=update
# 데이터베이스 방언 지정
spring.jpa.database-platform=org.hibernate.dialect.MySQLDialect
```


### build.gradle
```gradle
dependencies {
  # 
  implementation 'org.springframework.boot:spring-boot-starter-data-jpa' // JPA
  # 
  implementation 'org.springframework.boot:spring-boot-starter-web'
  # 
  implementation 'mysql:mysql-connector-java' // MySql
  # 
  compileOnly 'org.projectlombok:lombok'
  # 
  developmentOnly 'org.springframework.boot:spring-boot-devtools'
  # 
  annotationProcessor 'org.projectlombok:lombok'
  # 
  testImplementation 'org.springframework.boot:spring-boot-starter-test'

  # 그외 추가 가능함.


}

```
----



## 테이블 생성
### mysql GUI

### mysql Shell


### IntellJ

----



# 
