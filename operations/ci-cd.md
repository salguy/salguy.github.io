---
layout: default
title: CI/CD 구성
nav_order: 2
---

# 🔄 CI/CD 구성

살가이 프로젝트는 **GitHub Actions**를 활용하여 CI/CD 파이프라인을 구축했습니다.

## 주요 워크플로우

- 코드 push 시 자동 빌드 및 테스트
- main 브랜치에 병합될 경우 EC2 서버에 자동 배포 스크립트 실행
