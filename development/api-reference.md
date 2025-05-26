---
layout: default
title: API 명세서
nav_order: 5
---

# 📡 API 명세서

## 주요 엔드포인트

### POST `/upload_voice`
- 설명: 음성 파일 업로드
- 요청 형식: `multipart/form-data`
- 응답: 분석 결과(JSON)

### POST `/chat_with_llm`
- 설명: STT 결과 텍스트 기반 복약 정보 분석
- 요청: `{ text: "사용자 발화" }`
- 응답: `{ result: {...} }`

### PUT `/put_user_histories`
- 설명: 복약 여부 DB 저장
- 요청: `{ user_id, date, result }`

API 인증은 생략되었으나 향후 JWT 등으로 확장 가능.
