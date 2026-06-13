---
title: "Brain Storming with AI - 프로젝트 개요"
date: 2026-06-14T00:00:00+09:00
tags: ["project", "ai", "llm"]
---

## 프로젝트 개요

로컬 LLM 과 함께 브레인스토밍하고, 그 과정을 Wiki 로 관리하는 프로젝트입니다.

## 목표
1. 로컬 LLM 의 지식을 Wiki 로 축적
2. 반복적인 문제 해결 패턴 기록
3. 기술 결정 사항 (ADR) 관리
4. pi 에이전트와 연동하여 자동화

## 주요 기능
- **LLM Wiki**: Markdown 으로 지식 축적
- **RAG 대안**: 컴파일된 지식베이스
- **Git 버전 관리**: 모든 변경 사항 추적
- **GitHub Pages**: 무료 호스팅

## 기술 스택
- Hugo (정적 사이트 생성기)
- PaperMod 테마
- Git 버전 관리
- pi 에이전트 (Markdown 자동 생성)

## 폴더 구조
```
content/
├── posts/        # 블로그 포스트
└── wiki/         # LLM Wiki
    ├── errors/   # 오류 해결
    ├── decisions/# 아키텍처 결정
    ├── tools/    # 도구 사용법
    └── projects/ # 프로젝트별
```
