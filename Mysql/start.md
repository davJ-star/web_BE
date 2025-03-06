첫 글이다.


# mysql과 백엔드 연동
## root로 만드는데 에러가 생겨서 jsw 계정을 만들었다. (mysql shell)
[참고](https://jay-so.tistory.com/67)

```
[출처](https://kang-james.tistory.com/entry/MySQL-MySQL-CLI로-쉽게-다루기-MySQL-Shell-명령어-정리?category=893026)
1. \c --mysql [root]@localhost:[3306]
2. \sql
3. show databases; (만약 삭제하고 싶다면, drop database [db이름]; 생성하고 싶다면, create database [db이름]; )
(여기서는 생성: create database [db이름];)
4. use [db이름];
5. 테이블 생성
  ```
    create table member (
    -> student_id int primary key auto_increment
    -> student_name varchar(50)
    -> gender char(1),
    -> );

  ```
6. 테이블 목록 보기: show tables;


```


swJeong과
jsw만 지금 알고 있는 상태라서
나머지 계정 만들수 있는 것 어떻게 하는지 정리
----

## _cmd랑 powershell에서 만드는 방법 그리고 intellJ 터미널에서 만드는 방법_ (앞으로 이걸 더 많이 사용할 듯)



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
  # Spring Data "JPA"를 사용하여 "데이터베이스와 상호 작용"하기 위한 스타터 의존성입니다. "JPA(Java Persistence API)"를 사용하여 "객체-관계 매핑(ORM)"을 할 수 있게 해줍니다.
  implementation 'org.springframework.boot:spring-boot-starter-data-jpa' // JPA
  # Spring "Web"을 위한 스타터 의존성입니다. "Spring MVC를 사용"하여 "웹 애플리케이션을 구축"할 수 있게 해줍니다.
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



# db에서 엔티티의 관계
1:N 관계: 데이터베이스에서 하나의 엔티티가 여러 개의 다른 엔티티와 연결되는 관계

```paintext
## 1:N 관계: 데이터베이스에서 하나의 엔티티가 여러 개의 다른 엔티티와 연결되는 관계

**1:N 관계**는 데이터베이스에서 하나의 엔티티가 여러 개의 다른 엔티티와 연결되는 관계를 나타냅니다. 즉, 한쪽 엔티티는 여러 개의 다른 엔티티와 연결될 수 있지만, 반대쪽 엔티티는 오직 하나의 엔티티와만 연결될 수 있습니다.

**예시:**

* **고객과 주문:** 한 명의 고객은 여러 개의 주문을 할 수 있지만, 각 주문은 오직 한 명의 고객에게만 속합니다.
* **부서와 직원:** 한 부서에는 여러 명의 직원이 속할 수 있지만, 각 직원은 오직 하나의 부서에만 소속됩니다.
* **책과 저자:** 한 권의 책은 여러 명의 저자가 쓸 수 있지만, 각 저자는 한 권의 책에만 참여할 수 있습니다.

**데이터베이스 구현:**

1:N 관계는 데이터베이스에서 **외래 키(Foreign Key)**를 사용하여 구현됩니다. 외래 키는 한 테이블의 컬럼을 다른 테이블의 기본 키(Primary Key)와 연결하는 역할을 합니다.

**예시:**

* **고객 테이블(Customer)**: `customerId` (기본 키)
* **주문 테이블(Order)**: `orderId` (기본 키), `customerId` (외래 키, 고객 테이블의 `customerId`와 연결)

**장점:**

* **데이터 중복 방지:** 1:N 관계를 사용하면 동일한 정보를 여러 테이블에 저장할 필요가 없어 데이터 중복을 방지할 수 있습니다.
* **데이터 무결성 유지:** 외래 키를 사용하여 데이터 무결성을 유지할 수 있습니다. 예를 들어, 고객 테이블에서 고객 ID가 삭제되면 해당 고객 ID와 연결된 모든 주문 정보도 자동으로 삭제됩니다.
* **데이터 조회 및 업데이트 효율성 향상:** 1:N 관계를 사용하면 데이터 조회 및 업데이트를 효율적으로 수행할 수 있습니다.

**단점:**

* **데이터베이스 설계 복잡성:** 1:N 관계를 구현하려면 외래 키를 사용해야 하므로 데이터베이스 설계가 복잡해질 수 있습니다.
* **데이터 삭제 제약:** 외래 키 제약 조건으로 인해 데이터 삭제에 제약이 생길 수 있습니다. 예를 들어, 주문 테이블에서 고객 ID가 삭제된 경우, 해당 고객 ID와 연결된 모든 주문 정보도 삭제해야 합니다.

**결론:**

1:N 관계는 데이터베이스에서 하나의 엔티티가 여러 개의 다른 엔티티와 연결되는 관계를 나타내는 중요한 개념입니다. 외래 키를 사용하여 구현되며, 데이터 중복 방지, 데이터 무결성 유지, 데이터 조회 및 업데이트 효율성 향상 등의 장점을 제공합니다. 그러나 데이터베이스 설계 복잡성 및 데이터 삭제 제약과 같은 단점도 고려해야 합니다.


```
