---
layout: default
title: 🤖 AI 모델 및 프롬프트 설계
nav_order: 5
parent: 🛠 개발 가이드
description: "살가이 AI모델 개발 가이드"
permalink: /documents/developments/AImodel/
---

# 🤖 AI 모델 및 프롬프트 설계

## LLM (자연어 처리)
- 최종 모델: `MLP-KTLim/llama-3-Korean-Bllossom-8B`
- 평가 기준: 복약 여부 판단, 날짜 계산 정확도, 응답 품질
- 프롬프트는 `<json>`, `<response>` 태그로 출력 제한

### 프롬프트 구조

```json
<json>
{
  "복약여부": true,
  "복약시점": "2025-05-28 09:00",
  "기타": "두통을 호소함"
}
</json>

<response>
네, 오전 9시에 복약하셨습니다.
</response>
```