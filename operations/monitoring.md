
---

### 📄 `monitoring.md`

```markdown
---
layout: default
title: 서버 모니터링
nav_order: 3
---

# 📊 서버 모니터링

운영 중인 서버 상태를 실시간으로 모니터링하고 오류를 빠르게 감지하기 위해 ELK 스택 또는 간이 모니터링 툴을 적용했습니다.

## 로그 수집

- PM2 로그 디렉토리: `~/.pm2/logs`
- 서버 로그를 Filebeat 또는 custom 스크립트로 수집

## 시각화 도구

- ELK 스택 (Elasticsearch + Logstash + Kibana) 적용 예정
- Grafana + Loki 대안 구성 고려 중

## 실시간 알림

- 서버 상태 이상 시 Slack 또는 Discord 웹훅으로 알림 전송 예정
