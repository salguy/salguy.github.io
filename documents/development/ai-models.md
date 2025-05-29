---
layout: default
title: AI 모델
nav_order: 5
parent: "개발 가이드"
description: "살가이 AI모델 개발 가이드"
permalink: /documents/development/AImodel/
---

# 🤖 AI 모델 구조

## LLM (자연어 처리)
- 최종 모델: `MLP-KTLim/llama-3-Korean-Bllossom-8B`
- 평가 기준: 복약 여부 판단, 날짜 계산 정확도, 응답 품질
- 프롬프트는 `<json>`, `<response>` 태그로 출력 제한

## STT
- recognize-speech (라즈베리파이에서 실행)
- 녹음된 음성을 서버로 전송 후 처리

## TTS
- 서버에서 TTS 생성 후 음성 파일을 라즈베리파이에 반환
