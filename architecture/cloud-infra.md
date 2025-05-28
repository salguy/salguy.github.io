---
layout: default
title: 클라우드 인프라
nav_order: 3
---

# ☁️ 클라우드 인프라

## EC2 서버 (AWS)
- FastAPI 기반 REST API 서버
- React 기반 스피커 UI 호스팅
- SQLite 데이터베이스

## GCP 서버
- LLaMA 기반 LLM 모델 구동
- 자연어 분석 결과를 EC2로 반환

두 서버 간 통신은 REST API를 통해 이루어지며, 모델 추론과 데이터 처리를 분산하여 효율성을 확보합니다.