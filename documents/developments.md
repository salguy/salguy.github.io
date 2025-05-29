---
layout: default
title: 개발 가이드
nav_order: 3
has_children: true
description: 살가이 프로젝트 개발 가이드
permalink: /documents/developments/

---

# 🛠 개발 환경 설정

살가이 프로젝트의 개발을 위해 필요한 기본 환경은 다음과 같습니다.

## 공통 요구사항
- Python 3.10+
- Node.js 18+
- pip, npm

## 클라이언트(라즈베리파이)
- `recognize-speech` Python 패키지
- `arecord`, `pvporcupine`, `requests`, `pyaudio`
- `systemd` 혹은 `rc.local`을 통한 자동 실행 설정

## 서버(EC2)
- FastAPI
- SQLite
- PM2 (Node.js 앱 관리)

## 프론트엔드
- React + Vite + TailwindCSS
- Axios, Material UI

각 파트별 `setup.sh` 또는 README 파일 참고.
