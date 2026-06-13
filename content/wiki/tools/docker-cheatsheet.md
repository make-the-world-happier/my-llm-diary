---
title: "Docker 기본 명령어 모음"
date: 2026-06-14T00:00:00+09:00
tags: ["docker", "cheatsheet"]
---

## 컨테이너 관리

```bash
# 컨테이너 실행
docker run -d --name mycontainer nginx

# 컨테이너 중지
docker stop mycontainer

# 컨테이너 삭제
docker rm mycontainer

# 모든 컨테이너 삭제
docker rm -f $(docker ps -aq)
```

## 이미지 관리

```bash
# 이미지 빌드
docker build -t myimage:v1 .

# 이미지 삭제
docker rmi myimage:v1

# 모든 이미지 삭제
docker rmi -f $(docker images -aq)
```

## 볼륨

```bash
# 볼륨 생성
docker volume create myvolume

# 볼륨 마운트
docker run -v myvolume:/data nginx
```

## 네트워크

```bash
# 네트워크 생성
docker network create mynetwork

# 컨테이너 연결
docker network connect mynetwork mycontainer
```

## 문제 해결

```bash
# 컨테이너 로그 확인
docker logs mycontainer

# 컨테이너 내부 실행
docker exec -it mycontainer bash

# 컨테이너 상태 확인
docker ps -a
```
