
---

### 📄 `ci-cd.md`

```markdown
---
layout: default
title: CI/CD 구성
nav_order: 2
---

# 🔄 CI/CD 구성

살가이 프로젝트는 **GitHub Actions**를 활용하여 CI/CD 파이프라인을 구축했습니다.

## 주요 워크플로우

- 코드 push 시 자동 빌드 및 테스트
- main 브랜치에 병합될 경우 EC2 서버에 자동 배포 스크립트 실행 (향후 SSH 또는 rsync 방식 활용 예정)

### 예시 `.github/workflows/deploy.yml`

```yaml
name: Deploy Backend

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: SSH deploy
        run: |
          ssh user@ec2 'cd ~/salguy-backend && git pull && pm2 restart salguy-backend'
