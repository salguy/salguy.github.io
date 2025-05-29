---
layout: default
title: 서버 개발 가이드
nav_order: 3
parent: "개발 가이드"
description: "살가이 프로젝트 백엔드 개발 가이드"
permalink: /documents/development/backend/

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

## 🔄 CI/CD 구성

살가이 프로젝트는 **GitHub Actions**를 활용하여 CI/CD 파이프라인을 구축했습니다.

## 주요 워크플로우

- 코드 push 시 자동 빌드 및 테스트
- main 브랜치에 병합될 경우 EC2 서버에 자동 배포 스크립트 실행

## 실행 방식
- PM2를 통한 지속 실행
- 로그는 `~/.pm2/logs/`에서 확인 가능

## API 문서는 Swagger로 자동 생성됨: `/docs`
