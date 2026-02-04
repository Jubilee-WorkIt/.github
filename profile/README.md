# 💼 WorkIt - Job Marketplace Platform

> 2025 호주 글로벌 인턴십 프로젝트  
> 구직자와 구인자를 연결하는 구인구직 플랫폼

[![Build Status](https://img.shields.io/badge/build-passing-brightgreen)]()
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.5.9-brightgreen)]()
[![Java](https://img.shields.io/badge/Java-17-orange)]()
[![MySQL](https://img.shields.io/badge/MySQL-8.0-blue)]()

---

## 📋 목차

- [프로젝트 소개](#-프로젝트-소개)
- [주요 기능](#-주요-기능)
- [기술 스택](#-기술-스택)
- [시작하기](#-시작하기)
- [API 문서](#-api-문서)
- [프로젝트 구조](#-프로젝트-구조)
- [팀원](#-팀원)
- [라이선스](#-라이선스)

---

## 🎯 프로젝트 소개

**WorkIt**은 호주에서 일자리를 찾는 워킹홀리데이 학생 구직자와 인재를 찾는 현지 구인자를 연결하는 구인구직 플랫폼입니다.

### 핵심 가치

- 🔍 **쉬운 검색**: 지역, 카테고리, 근무 형태별로 빠르게 공고 검색
- 🗺️ **지도 기반**: 근처 공고를 지도에서 한눈에 확인
- 💬 **실시간 채팅**: 구직자와 구인자가 직접 소통
- 📄 **이력서 관리**: 한 번 작성한 이력서로 여러 공고에 지원

---

## ✨ 주요 기능

### 1. 인증 & 회원 관리
- ✅ 이메일 회원가입/로그인
- ✅ Google OAuth 소셜 로그인
- ✅ Apple 로그인 (준비 중)
- ✅ JWT 기반 인증
- ✅ 역할 선택 (구직자/구인자)

### 2. 공고 관리
- ✅ 공고 목록 조회 (HOT, 최신, 장기/단기)
- ✅ 검색 & 필터링 (지역, 카테고리)
- ✅ 지도 기반 근처 공고 검색
- ✅ 공고 상세 정보
- ✅ 공고 찜하기 (북마크)

### 3. 지원 관리
- ✅ 공고 지원하기
- ✅ 지원 내역 조회
- ✅ 지원 취소

### 4. 이력서
- ✅ 이력서 작성 & 수정
- ✅ PDF 업로드
- ✅ 이력서 조회 & 삭제

### 5. 실시간 채팅
- ✅ 1:1 채팅 (WebSocket)
- ✅ 채팅방 목록
- ✅ 읽음 처리
- ✅ 미읽음 메시지 개수

### 6. 알림
- ✅ 알림 목록 조회
- ✅ 읽음 처리
- ✅ 미읽음 개수

### 7. 프로필
- ✅ 프로필 조회 & 수정
- ✅ 선호 설정 저장 (직종, 근무 형태, 희망 시급)
- ✅ 지역 설정

---

## 🛠 기술 스택

### Backend
- **Framework**: Spring Boot 3.5.9
- **Language**: Java 17
- **Build**: Gradle 8.14.3
- **ORM**: Spring Data JPA / Hibernate

### Database
- **RDBMS**: MySQL 8.0
- **Host**: AWS EC2 (52.79.240.230)

### Security
- **Authentication**: JWT (JSON Web Token)
- **Password**: BCrypt

### Real-time
- **WebSocket**: Spring WebSocket + STOMP
- **Protocol**: SockJS

### API Documentation
- **Tool**: SpringDoc OpenAPI (Swagger UI)

### Deployment
- **Container**: Docker
- **Orchestration**: Docker Compose
- **Server**: AWS EC2

---

## 🚀 시작하기

### 필수 요구사항

- Java 17 이상
- Gradle 8.14.3 이상
- MySQL 8.0 (또는 접속 가능한 DB 서버)

### 설치 및 실행

#### 1. 레포지토리 클론

```bash
git clone https://github.com/Jubilee-WorkIt/workit-backend.git
cd workit-backend
```

#### 2. 환경 변수 설정

```bash
# application.yaml 또는 환경 변수 설정
export JWT_SECRET=your-secret-key-min-256-bits
export GOOGLE_CLIENT_ID=your-google-client-id
export APPLE_CLIENT_ID=your-apple-client-id
```

---

## 📚 API 문서

### Swagger UI

**개발 환경**:
```
http://localhost:8080/swagger-ui/index.html
```

**프로덕션 환경**:
```
https://api-workit.mmhs.app/swagger-ui/index.html
```

### OpenAPI JSON

```
GET /v3/api-docs
```

### 주요 엔드포인트

| 카테고리 | 메서드 | 경로 | 설명 |
|---------|--------|------|------|
| **인증** | POST | `/api/auth/signup` | 회원가입 |
| | POST | `/api/auth/login` | 로그인 |
| | POST | `/api/auth/google` | Google 로그인 |
| | POST | `/api/auth/role` | 역할 선택 |
| **공고** | GET | `/api/jobs` | 공고 목록 |
| | GET | `/api/jobs/hot` | HOT 공고 |
| | GET | `/api/jobs/nearby` | 근처 공고 |
| | GET | `/api/jobs/{id}` | 공고 상세 |
| **지원** | POST | `/api/jobs/{id}/apply` | 공고 지원 |
| | GET | `/api/applications` | 지원 내역 |
| **찜** | POST | `/api/bookmarks/{jobId}` | 찜하기 |
| | GET | `/api/bookmarks` | 찜 목록 |
| **이력서** | GET | `/api/resumes/me` | 내 이력서 |
| | POST | `/api/resumes` | 이력서 작성 |
| **채팅** | GET | `/api/chat/rooms` | 채팅방 목록 |
| | POST | `/api/chat/rooms` | 채팅방 생성 |
| | WS | `/ws-chat` | WebSocket 연결 |
| **알림** | GET | `/api/notifications` | 알림 목록 |
| | GET | `/api/notifications/unread-count` | 미읽음 개수 |

---

## 🚦 API 응답 코드

| 코드 | 상태 | 설명 |
|------|------|------|
| 200 | OK | 요청 성공 |
| 201 | Created | 리소스 생성 성공 |
| 204 | No Content | 요청 성공 (응답 바디 없음) |
| 400 | Bad Request | 잘못된 요청 |
| 401 | Unauthorized | 인증 실패 |
| 403 | Forbidden | 권한 없음 |
| 404 | Not Found | 리소스 없음 |
| 409 | Conflict | 중복 리소스 |
| 500 | Internal Server Error | 서버 오류 |

---

## 👥 팀원

### Backend

- **Sangyeon Lee** -
- Email: sanoni0115@gmail.com
- GitHub: [@sangyeon08](https://github.com/sangyeon08)

### Frontend

- **Hyoeun Lee**
- Email:
- GitHub: [@ID](link)
  
### Designer

- **Mijoo Park**
- Email: 
- Instagram: [@ID](link)
  

---

<p align="center">
  Made with ❤️ by Jubilee Team
</p>

<p align="center">
  © 2025 WorkIt. All rights reserved.
</p>
