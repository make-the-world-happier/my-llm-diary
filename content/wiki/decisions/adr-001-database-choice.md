---
title: "ADR-001: 데이터베이스 선택 - PostgreSQL"
date: 2026-06-14T00:00:00+09:00
tags: ["database", "postgresql", "architecture"]
---

## 상황

프로젝트에 적합한 데이터베이스를 선택해야 함.

## 고려사항
- 관계형 데이터 필요
- JSON 지원
- 확장성
- 로컬 실행 가능성

## 결정

**PostgreSQL** 을 선택함.

## 이유
1. 강력한 관계형 기능
2. JSONB 필드로 반구조화 데이터 지원
3. 확장성이 우수
4. 로컬에서 쉽게 실행 가능 (Docker)
5. 오픈소스이며 커뮤니티가 큼

## 대안
- MySQL: JSON 지원이 제한적
- MongoDB: 관계형 쿼리가 필요함
- SQLite: 확장성 부족

## 참고
- Docker 로 로컬 환경 구성: `docker run -d -p 5432:5432 -e POSTGRES_PASSWORD=secret postgres`
