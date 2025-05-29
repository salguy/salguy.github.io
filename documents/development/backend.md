---
layout: default
title: 🔧백엔드 개발 가이드
nav_order: 3
parent: 🛠 개발 가이드
description: "살가이 프로젝트 백엔드 개발 가이드"
permalink: /documents/developments/backend/

---

# 🔧 백엔드 개발 가이드

## 서버 구조
- FastAPI 기반 REST API 서버  
- [API 명세서 보러 가기](api-reference.md)

## 주요 워크플로우

- main 브랜치에 코드 push 시 EC2 서버에 자동 배포 스크립트 실행

## 실행 방식
- PM2를 통한 지속 실행
- 로그는 `~/.pm2/logs/`에서 확인 가능

