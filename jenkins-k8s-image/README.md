# Custom Jenkins on Kubernetes
## 서버/인프라 공부 시작 10/20~
##2026-02-03 - jenkins k8s환경에서 배포 test

## 개요
쿠버네티스 환경에서 도커 이미지 빌드 및 배포가 가능한 커스텀 젠킨스 이미지 구축 프로젝트

## 해결안된 주요 이슈
Docker in Docker (DooD) 권한 문제
   - 젠킨스 파드 내부에서 `docker` 명령어를 쓰기 위해 호스트의 `docker.sock`을 마운트함.
   - 호스트와 컨테이너 간의 GID 불일치 문제를 해결하기 위해 빌드 시점에 `HOST_GID`를 변수로 받아 그룹 권한을 동적으로 설정함. 
   - 테스트 결과 개같이 실패.. chmod 666으로 임시 해결 / 해결방안 찾아보기

## 주요 기술 스택
- Docker, Kubernetes, Jenkins, Shell Script (Bash)

##Docker socket permission denied 이슈를 chmod 666으로 임시 해결 / 해결방안 찾아보기

---

# Jenkins Study
##2026-04-15 수정
Kubernetes 환경에서 Jenkins를 배포하고 GitHub 연동 및 CI 작업을 수행하기 위한 커스텀 Jenkins 이미지입니다.

## 포함 도구
- Jenkins LTS
- Git
- Curl
- kubectl v1.28.15

## 목적
- Kubernetes 클러스터 내 Jenkins 배포
- GitHub 소스 연동
- 추후 Kubernetes 배포 자동화 실습
