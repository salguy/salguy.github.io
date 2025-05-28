---
layout: default
title: 배포 가이드
nav_order: 1
---

# 🚀 배포 가이드

살가이 프로젝트는 **EC2**에서 백엔드와 프론트엔드를 통합 배포하며, **GCP**에서는 LLM 추론 서버를 운영합니다.

## EC2 서버 배포

- 백엔드 서버: FastAPI 앱 → PM2로 실행
- 프론트엔드 앱: React → Vite 빌드 후 정적 파일 서빙

### 기본 배포 명령어 예시

```bash
cd backend
pm2 start main.py --interpreter=python3 --name=salguy-backend

