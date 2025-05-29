---
layout: default
title: ⚙️개발 환경 설정
parent: 🛠 개발 가이드
nav_order: 1
description: "살가이 프로젝트 개발 환경 설정"
permalink: /documents/developments/setup/
---

# ⚙️ 개발 환경 설정

살가이 프로젝트의 개발을 위해 필요한 기본 환경은 다음과 같습니다.

## 공통 요구사항
- Python 3.10+
- Node.js 18+
- pip, npm

## [클라이언트(라즈베리파이)](/documents/developments/hardware/)
```bash

# 저장소 클론
git clone https://github.com/salguy/HW.git
cd HW

# Python 의존성 설치
pip install -r requirements.txt

#프로그램 실행
python main.py
```
- 추가사항: `systemd` 혹은 `rc.local`을 통한 자동 실행 설정

## [백엔드 서버(EC2)](/documents/developments/backend/)
- FastAPI
- SQLite
- PM2 (Node.js 앱 관리)
- 프론트엔드 정적 배포

### 백엔드 개발 환경 세팅

```bash
# 저장소 클론
git clone https://github.com/salguy/APP.git
cd APP

# Python 의존성 설치
pip install -r requirements.txt


# 서버 실행 및 PM2로 프로세스 관리
pm2 start "python main.py" --name main

```

## [AI서버 (GCP)](/documents/developments/AImodel/)

### AI서버 개발 환경 세팅

```bash
# 저장소 클론
git clone https://github.com/salguy/AI.git
cd AI

# Python 의존성 설치
pip install -r requirements.txt


# 서버 실행 및 PM2로 프로세스 관리
pm2 start "python main.py" --name salguy

```
