---
layout: default
title: 🛠 개발 가이드
nav_order: 3
has_children: true
description: 살가이 프로젝트 개발 전반을 위한 단계별 개발 가이드
permalink: /documents/developments/
---

# 🧑‍💻 개발 가이드

이 문서는 **살가이 프로젝트**의 전체 시스템 구성과 개발 과정을 체계적으로 소개합니다.  
프론트엔드, 백엔드, AI 모델, 하드웨어, 클라우드 인프라까지 살가이의 기술적 핵심 요소들을 이해하고, 직접 구현할 수 있도록 단계별로 안내합니다.

---

## 📁 프로젝트 구조 요약

살가이는 다음과 같은 세 가지 핵심 컴포넌트로 구성됩니다:

- **라즈베리파이 (RPi)**: 사용자 인터페이스를 담당하며, 음성 감지, 녹음, 복약 알림 등 직접적인 상호작용 기능을 수행합니다.
- **EC2 서버**: FastAPI 기반의 백엔드 서버로, STT 및 TTS 요청 처리, 사용자 정보 및 복약 이력 저장, 프론트엔드 호스팅을 담당합니다.
- **GCP 서버**: LLaMA 기반 LLM 모델을 탑재한 추론 서버로, 복약 여부 및 건강 관련 발화 분석을 처리합니다.

모든 컴포넌트는 REST API 기반으로 통신하며, 고령자 친화성과 실시간 응답성을 고려하여 설계되었습니다.

![살가이 아키텍처 다이어그램](/assets/images/살가이 아키텍처 다이어그램.drawio.png)
그림-살가이 아키텍처 다이어그램
---

## 🔧 1. 시작에 앞서

### 📌 공통 개발 환경

[개발 환경 설정법](setup)
- Python 3.10 이상  
- Node.js 18 이상  
- pip / npm  
- pm2 (백엔드 프로세스 관리용)

### ☁️ 클라우드 인프라 구성

| 구성 요소 | 플랫폼 | 역할 |
|-----------|----------|------|
| EC2       | AWS     | 백엔드 API 서버 및 프론트엔드 정적 파일 호스팅 |
| GCP       | Google  | LLM 기반 AI 추론 서버 |
| RPi       | 로컬    | 사용자 음성 인터페이스 및 디바이스 제어 |

### 🔁 전체 데이터 흐름

```text
[RPi]
 ↓ 녹음
[EC2 - STT 처리 및 API]
 ↓ 텍스트
[GCP - LLM 분석]
 ↓ 텍스트
[EC2 - 파싱 및 TTS 생성]
 ↓ 음성
[RPi - 음성 피드백 재생]
```

이 구조는 각 기능이 독립적으로 작동하면서도 REST API를 통해 유기적으로 연결되도록 구성되어 있어, 기능 확장이나 유지보수에 유리합니다.

---

## [⚙️ 2. 백엔드 (FastAPI)](backend)

[살가이 프로젝트 백엔드 Github](https://github.com/salguy/APP)

살가이의 백엔드 서버는 FastAPI 기반으로 구축되었으며, 사용자 인증부터 음성 데이터 처리까지 다양한 기능을 제공합니다.

- **주요 역할**:
  - 사용자 등록 및 인증
  - 복약 기록 및 스케줄 관리
  - STT 데이터 수신 및 TTS 파일 반환
  - LLM 처리 위해 GCP 서버와 통신
- **데이터베이스**: 현재는 SQLite 사용 (가볍고 관리 용이).  
  향후 안정성과 확장성을 고려해 PostgreSQL 이관을 검토 중입니다.

---

## [🎨 3. 프론트엔드 (React + Vite + TailwindCSS)](frontend)

[살가이 프로젝트 프론트엔드 Github](https://github.com/salguy/Front-end)

프론트엔드는 React와 Vite, TailwindCSS 기반으로 구축되어 있으며, 고령 사용자를 고려한 **키오스크 스타일의 UI**를 제공합니다.

- **주요 특징**:
  - 단순하고 명확한 버튼 중심의 UI
  - 복약 시간 표시 및 피드백 기능
  - 어르신들께 최적화된 인터페이스 구성

디자인은 Material UI와 TailwindCSS를 혼합해 사용하여, 빠른 개발과 유연한 스타일링이 가능하도록 했습니다.

---

## [🧠 4. AI 서버 및 모델 (GCP 기반)](AImodel)

[살가이 프로젝트 AI서버 및 모델 Github](https://github.com/salguy/AI)

살가이의 핵심 분석 기능은 GCP에 위치한 AI 추론 서버에서 수행되며, LLaMA 기반 LLM을 활용합니다.

- **사용 모델**: `MLP-KTLim/llama-3-Korean-Bllossom-8B`
- **운영 방식**: GCP VM 인스턴스에서 FastAPI 기반 추론 API 실행

### 🤖 주요 기능

- 자연어 발화로부터 복약 여부(T/F), 시점 추론
- 상황 분류(Text Classification)를 통한 프롬프트 자동 선택
- 상황에 알맞은 답변

이 구조는 복잡한 명령어 없이도 자유로운 사용자 응답 처리를 가능하게 하며, 실제 대화에 가까운 자연스러운 상호작용을 구현할 수 있습니다.

---

## [🔌 5. 하드웨어 연동 (라즈베리파이)](hardware)

[살가이 프로젝트 하드웨어 Github](https://github.com/salguy/HW)

라즈베리파이는 살가이 시스템의 프론트라인 디바이스로, 실제 사용자가 마주하는 인터페이스 역할을 합니다.

- **통합 장치**:
  - 마이크 (`arecord`, `pyaudio`) — 음성 녹음
  - 스피커 (`mpg123`, `aplay`) — 음성 피드백 재생
  - Wake Word 감지 (`pvporcupine`) — “살가이”
  - LED, 버튼, 디스플레이 — 시각적 피드백 및 상호작용

### 📋 복약 루틴 처리 흐름

1. 스피커가 인사
2. 식사 여부 확인
3. 복약 시각 알림
4. 5분 후 복약 여부 재확인
5. 미응답 또는 미복약 시 10분 간격 3회 추가 확인

Wake Word와 복약 루틴은 비동기적으로 실행되며, 마이크 자원 충돌 방지를 위해 `mic_lock` 동기화 처리가 구현되어 있습니다.

---

## ✅ 마무리

이 개발 가이드는 살가이 프로젝트의 전반적인 기술 구조를 이해하고, 직접 개발 환경을 구성하거나 기능을 확장하고자 하는 개발자에게 실질적인 정보를 제공합니다.  
전체 흐름을 단계적으로 따라가면, 복약 알림 AI 스피커 시스템을 완성도 있게 구현하고 안정적으로 운영할 수 있습니다.
