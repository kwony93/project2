# 2차 프로젝트

## 환경
- Kubernetes Cluster (On-Premise)
- Jenkins (CI/CD)
- Docker / Docker Hub
- Spring PetClinic (WAS) -> 다른 app도 가능하게 만들기

---

## Jenkins Pipeline 주요 단계

- STAGE.1 : Source Checkout  
- STAGE.2 : Maven Build  
- STAGE.3 : Docker Build  
- STAGE.4 : Docker Push  
- STAGE.5 : Kubernetes Deploy  

---

## 배포 방식

- Docker 이미지에 BUILD_NUMBER 태그 적용
- kubectl set image 명령어를 통해 Deployment 업데이트
- Rolling Update 방식으로 무중단 배포 수행

---

## 현재까지 진행 상황

- 빌드 후 파드에서 이미지파일 빌드번호랑 같음을 확인
- 불필요한 테스트 과정은 검증만 하고 정리 (Git / Docker / Kubeconfig)
- DNS로 jenkins.user3.goping.com / was.user3.goping.com 으로 접속 가능 ( 외부에서는 아직 X)

---

## 향후 계획
spring-petclinic에서 다른 app으로 변경
DB 추가
프로메테우스+그라파다 따로 공부해서 구축하기
외부에서 WAS 접근 가능하게 하기 ( DNS 외부 존 수정 + 라우터 PAT 추가)
