---
layout: default
title: API 명세서
---

# 📡 API 명세서

살가이 프로젝트의 서버는 FastAPI 기반 REST API 서버입니다. 라즈베리파이, EC2, GCP 간의 통신을 REST API로 처리하며, 사용자 관리, 복약 루틴 기록, 음성 처리 기능 등을 제공합니다.

---

## 👤 Users: 회원 기능

| Method | Endpoint | 설명 |
|--------|----------|------|
| `POST` | `/api/user/signup` | 사용자 등록 (이름, 비밀번호 등록) |
| `POST` | `/api/user/login` | 로그인 요청 (토큰 발급 또는 인증 확인) |
| `GET`  | `/api/user/verify` | 사용자 인증 상태 확인 |
| `GET`  | `/api/user/me` | 현재 로그인한 사용자 정보 조회 |
| `PUT`  | `/api/user/histories` | 복약 시각 기록 저장 (STT → LLM 분석 후 전달) |
| `GET`  | `/api/user/histories` | 사용자 복약 이력 조회 (관리자 앱 표시용) |
| `POST` | `/api/users/schedules` | 복약 스케줄 등록 (시간, 복약 내용 등) |
| `GET`  | `/api/users` | 전체 사용자 목록 조회 (관리자용) |
| `DELETE` | `/api/users` | 사용자 계정 삭제 요청 |

---

## 💊 Medications: 약 정보 관리

| Method | Endpoint | 설명 |
|--------|----------|------|
| `GET`  | `/api/medications` | 약 정보 목록 조회 |
| `POST` | `/api/medications` | 약 정보 등록 (예: 고혈압약, 당뇨약 등) |
| `DELETE` | `/api/medications` | 약 정보 삭제 |

---

## 🧠 STT: 음성 인식 (Speech-to-Text)

| Method | Endpoint | 설명 |
|--------|----------|------|
| `POST` | `/api/stt` | 음성 데이터를 서버로 전송하고 텍스트로 변환된 결과를 반환함<br>→ 라즈베리파이에서 `arecord`로 녹음 후 전송 |

---

## 🔊 TTS: 음성 피드백 생성 (Text-to-Speech)

| Method | Endpoint | 설명 |
|--------|----------|------|
| `POST` | `/api/tts` | 텍스트를 서버에서 음성으로 변환하여 파일(.wav)로 반환함<br>→ 복약 알림, 음성 응답 등에서 사용 |

---

## 🧪 Test: 테스트 및 이벤트

| Method | Endpoint | 설명 |
|--------|----------|------|
| `POST` | `/api/wake` | Wake Word 감지 시 서버 호출 테스트 |
| `GET`  | `/api/events/{user_id}` | SSE 기반 실시간 이벤트 스트림 수신 |
| `POST` | `/api/test` | 1차 통합 테스트용 |
| `POST` | `/api/test2` | 2차 통합 테스트용 |
| `POST` | `/api/FEtest` | 프론트엔드 통신 테스트용 엔드포인트 |

---

## 🌐 Default (React 앱 정적 라우팅 지원)

| Method | Endpoint | 설명 |
|--------|----------|------|
| `GET` | `/test/{full_path}` | React SPA 라우팅을 위한 정적 경로 대응 |
| `GET` | `/test` | 기본 정적 경로 반환 |

---

> ✅ 대부분의 API는 토큰 인증 없이 동작하지만, 추후 JWT 인증 방식 추가 예정입니다.  
> ✅ 모든 POST 요청은 JSON 형식의 body를 포함하며, 파일 전송 시 multipart/form-data 사용합니다.
