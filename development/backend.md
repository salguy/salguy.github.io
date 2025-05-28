---
layout: default
title: 서버 및 API 명세서
nav_order: 4
---

# 🔧 백엔드 개발

## 서버 구조
- FastAPI 기반 REST API 서버
- 주요 라우팅:
  - `/chat_with_llm`: 텍스트 분석 요청
  - `/put_user_histories`: 복약 여부 저장

## 주요 라이브러리
- fastapi
- pydantic
- uvicorn

## 실행 방식
- PM2를 통한 지속 실행
- 로그는 `~/.pm2/logs/`에서 확인 가능

## API 문서는 Swagger로 자동 생성됨: `/docs`
