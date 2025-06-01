# 🚀 Backend Development Hub



**"Architecture First, Iterative Optimization, Security Focus, Scalability"**



## 📋 Repository Overview

이 저장소는 **백엔드 개발 최적화**와 **컴퓨터 사이언스 관점**에서의 메모 및 프로젝트 연결(적용) 리뷰를 위한 공간입니다. 실무 중심의 백엔드 아키텍처 설계와 성능 최적화에 중점을 둡니다.

### 🎯 Learning Philosophy
- **Architecture First**: 확장 가능한 시스템 설계 우선
- **Iterative Optimization**: 지속적인 성능 개선
- **Security Focus**: 보안을 고려한 개발
- **Scalability**: 대용량 트래픽 처리 능력

## 🛠 Technology Stack





### **Backend Frameworks**
- **Spring Boot 3.0+**
  - Spring Security
  - Spring Data JPA
  - Spring MVC
  - MyBatis
- **Python Frameworks**
  - Django REST Framework
  - FastAPI
  - Flask
- **Node.js**
  - Express.js




### **Databases & ORM**
- **Relational DB**
  - MySQL 8.0+
  - MariaDB
  - Oracle
  - PostgreSQL
  - SQLite
- **ORM/Persistence**
  - JPA/Hibernate
  - MyBatis
  - JDBC Template




### **DevOps & Tools**
- **Containerization**
  - Docker
  - Kubernetes (학습중)
- **CI/CD**
  - GitHub Actions
  - Jenkins (학습중)
- **Monitoring**
  - Prometheus (학습중)
  - Grafana (학습중)





## 🗄️ Database Optimization

### **MySQL Performance Tuning**

```sql
-- 복합 인덱스 최적화로 쿼리 성능 향상
CREATE INDEX idx_patient_medication 
ON prescriptions(patient_id, medication_time DESC) 
INCLUDE (dosage, status);
```

### **Connection Pool & Caching**
- **Redis**: API 응답 캐싱으로 응답시간 개선 (도입 예정)
- **HikariCP**: Connection Pool 최적화
- **Database Indexing**: 쿼리 성능 최적화

## 📊 Performance Metrics

| Metric | Target | Current Status | Goal |
|--------|--------|----------------|------|
| API Latency |  80% | 구현 중 | 테스트 강화 |

## 🚀 Featured Projects

### 🤖 **1. AI-Powered Attendance Management System**
**Tech Stack**: Django + Next.js + AI/ML + OpenCV

**Key Features**:
- 실시간 얼굴인식 기반 출석 체크
- 출결 현황 통계 및 분석 데이터 제공
- 관리자 페이지용 API (사원 관리, 지각률 분석)
- 출결 캘린더 및 히트맵 데이터 처리

**Performance**:
- 얼굴인식 정확도 **95%** 달성
- 동시 접속자 **100명** 처리 가능
- 관리자 업무 시간 **70%** 단축

```java
// Spring Boot 버전으로 구현시 JPA Batch Insert 최적화
@Transactional
public void bulkInsertAttendance(List attendances) {
    final int BATCH_SIZE = 100;
    for (int i = 0; i  0) {
            entityManager.flush();
            entityManager.clear();
        }
    }
}
```

🔗 [Repository](https://github.com/davJ-star/attendance-management-nextjs)

### 💊 **2. Smart Medication Management Platform**
**Tech Stack**: Spring Boot + FastAPI + AI Integration

**Architecture Highlights**:
- **Microservices**: Spring Boot + FastAPI 하이브리드 아키텍처
- **AI Integration**: OCR + LLM 기반 의약품 정보 추출
- **Real-time Notifications**: 복용 스케줄 관리 및 알림
- **Family Sharing**: 가족 간 건강 정보 공유 시스템

**Performance**:
- OCR 인식 정확도 **90%** 달성
- API 호출 비용 **40%** 절감
- 복용 준수율 **30%** 향상
- 의약품 정보 입력 시간 **80%** 단축

🔗 [Repository](https://github.com/davJ-star/hanwha-ieum-seongwook)

### 📝 **3. Community Board System (SIAT Blog)**
**Tech Stack**: Spring Boot + Oracle + JWT + MyBatis

**Security Features**:
```java
@RestController
@RequestMapping("/api/auth")
public class AuthController {
    
    @PostMapping("/login")
    public ResponseEntity authenticateUser(@Valid @RequestBody LoginRequest loginRequest) {
        Authentication authentication = authenticationManager.authenticate(
            new UsernamePasswordAuthenticationToken(loginRequest.getUsername(), loginRequest.getPassword())
        );
        
        String jwt = jwtUtils.generateJwtToken(authentication);
        return ResponseEntity.ok(new JwtResponse(jwt));
    }
}
```

**Key Features**:
- JWT 기반 무상태 인증 시스템
- 역할 기반 접근 제어 (RBAC)
- 실시간 코드 리뷰 게시판
- RESTful API 설계 및 Swagger 문서화

🔗 [Repository - Version 1](https://github.com/siat-blog/siat9-blog)
🔗 [Repository - Frontend](https://github.com/davJ-star/siatPosts-FE)
🔗 [Repository - Backend MVP](https://github.com/davJ-star/siatPostMvp-BE)

### 📚 **4. Used Bookstore Management System**
**Tech Stack**: Java + Oracle + JDBC + 알라딘 API

**Database Design**:
- ERD 설계 및 정규화 (3NF)
- 알라딘 API 연동으로 실시간 도서 정보 동기화
- 트랜잭션 관리로 주문 처리 안정성 확보
- Factory Pattern 적용으로 객체 생성 최적화

**Core Features**:
- 도서 검색 및 정보 관리
- 주문 처리 및 재고 관리
- 회원 관리 및 구매 이력
- 장바구니 및 위시리스트

🔗 [Repository](https://github.com/siatBooks/books)

### ✅ **5. Todo Management System**
**Tech Stack**: Spring Boot + MySQL + MyBatis + Bean Validation

**Implementation Highlights**:
- Todo CRUD API 구현
- Bean Validation 기반 데이터 유효성 검증
- 세션 기반 사용자 관리
- RESTful API 설계 원칙 적용
- Swagger API 문서화

🔗 [Repository](https://github.com/davJ-star/siat-springboot)

### 👥 **6. User Management System**
**Tech Stack**: Spring Boot + JPA/Hibernate + Spring Security + BCrypt

**Security Implementation**:
```java
@Configuration
@EnableWebSecurity
public class SecurityConfig {
    
    @Bean
    public PasswordEncoder passwordEncoder() {
        return new BCryptPasswordEncoder();
    }
}
```

**Key Features**:
- Spring Security 기반 인증/인가
- BCrypt 패스워드 암호화
- JPA Entity 설계 및 관계 매핑
- 사용자 권한 관리 시스템

🔗 [Repository](https://github.com/side-projectFOR/members)

### 🛒 **7. E-commerce Platform**
**Tech Stack**: Next.js + TypeScript + Tailwind CSS

**Frontend Features**:
- 고성능 서버 렌더링 Next.js App Router
- TypeScript 기반 타입 안전성
- Tailwind CSS 반응형 디자인
- 상품 관리 및 결제 시스템

🔗 [Repository](https://github.com/davJ-star/nextjs-commerce)

### 🌱 **8. First Spring Starter**
**Tech Stack**: Spring Boot + Java

**Learning Project Features**:
- Spring Framework 기초 학습
- MVC 패턴 구현
- Dependency Injection 이해
- Repository Pattern 적용

🔗 [Repository](https://github.com/davJ-star/first-spring-starter)

## 🏗 System Architecture & Design Patterns

### **Database Design Principles**
- 정규화 3NF 적용으로 데이터 무결성 확보
- 인덱싱 전략으로 쿼리 성능 최적화
- 외래키 제약조건으로 참조 무결성 보장
- 트랜잭션 관리로 ACID 속성 준수

## 🔒 Security Implementation

### **Authentication & Authorization**
- JWT 토큰 기반 무상태 인증
- Spring Security 통합
- BCrypt 암호화
- RBAC (Role-Based Access Control)

### **Data Protection**
- SQL Injection 방지를 위한 Prepared Statement
- CORS 설정으로 크로스 도메인 보안 관리
- HTTPS 통신 강제화
- 입력 데이터 유효성 검증

## 🔧 Development Tools & Practices

### **Code Quality**
- **Code Review**: 주 10건 이상 참여
- **Documentation**: API 명세서 작성

### **API Documentation**
- **Swagger/OpenAPI**: 100% 문서화 완성도
- **Postman Collections**: API 테스트 자동화 (도입 예정)

### **Version Control**
- **Git**: 브랜치 전략 및 커밋 컨벤션
- **GitHub**: 코드 리뷰 및 이슈 관리

## 🎓 Learning Resources

### **Currently Studying**
- **Microservices Patterns**: 분산 시스템 설계
- **Event Sourcing**: 이벤트 기반 아키텍처
- **CQRS**: 명령과 조회 분리
- **Kubernetes**: 컨테이너 오케스트레이션

### **Recommended Books**
- "Designing Data-Intensive Applications"
- "Spring Boot in Action"
- "Database Internals"
- "Clean Architecture"

## 📈 Roadmap

### **Q2 2025**
- [ ] Kubernetes 기반 마이크로서비스 배포
- [ ] Event Sourcing 패턴 적용
- [ ] GraphQL API 도입
- [ ] Redis 캐싱 전략 구현

### **Q3 2025**
- [ ] Serverless Architecture 연구
- [ ] ML Pipeline 통합
- [ ] Multi-region 배포
- [ ] 모니터링 시스템 구축

### **Q4 2025**
- [ ] 성능 최적화 고도화
- [ ] 보안 강화
- [ ] 대용량 데이터 처리
- [ ] 실시간 데이터 스트리밍
