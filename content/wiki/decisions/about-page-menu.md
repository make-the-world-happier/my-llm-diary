---
title: "About 페이지 메뉴 추가"
date: 2026-06-14T00:00:00+09:00
tags: ["ui", "menu", "navigation"]
---

## 개요

Hugo 메뉴에 About 페이지를 추가하여 사용자가 프로젝트 개요를 쉽게 찾을 수 있도록 합니다.

## 문제점

- `content/about.md` 파일이 존재했지만 메뉴에 표시되지 않음
- 사용자가 About 페이지를 찾기 어려움
- 블로그/포털에서 About 페이지는 표준적인 네비게이션 항목

## 해결 방안

`hugo.toml` 에 About 메뉴 항목을 추가합니다:

```toml
[menu]
  [[menu.main]]
    identifier = 'posts'
    name = 'Posts'
    pageRef = 'posts'
    weight = 10
  [[menu.main]]
    identifier = 'wiki'
    name = 'Wiki'
    pageRef = 'wiki'
    weight = 20
  [[menu.main]]
    identifier = 'about'
    name = 'About'
    pageRef = 'about'
    weight = 30
```

## 결과

- 헤더 메뉴에 About 버튼이 Posts, Wiki 다음에 표시됨
- PaperMod 테마에서 자동으로 렌더링됨
- `weight=30` 으로 Posts(10), Wiki(20) 다음 위치

## 참고

- Hugo 메뉴 시스템: `menu.main` 에 항목 추가만으로 자동 렌더링
- PaperMod 테마: 기본 헤더 레이아웃이 메뉴 항목을 자동으로 표시
