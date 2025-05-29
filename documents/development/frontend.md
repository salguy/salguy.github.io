---
layout: default
title: 🎨스피커 UI 개발 가이드
nav_order: 2
parent: 🛠 개발 가이드
description: "살가이 스피커 UI 개발 가이드"
permalink: /documents/developments/frontend/
---

# 🎨 스피커 UI 개발 가이드

React 기반의 자막을 표기하는 스피커의 UI입니다.

## 주요 기술 스택
- React + Vite + TailwindCSS
- TypeScript
- Material UI
- Axios (REST API 연동)

## 페이지 구성
- 홈 화면 (자막)
- 알림 설정/관리 페이지(개발예정)

### 실행 및 배포

```bash
npm run dev          # 개발용 실행
npm run build        # 정적 파일 빌드
cp -r dist/ <FastAPI_main.py_directory>  # EC2에 배포 시
```

또는 FastAPI 내 정적 라우터 사용(해당 방법으로 배포):

```python
app.mount("/", StaticFiles(directory="frontend/dist", html=True), name="static")
```

