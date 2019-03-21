# withkid-backend-structure
백엔드 워크플로우
![backend workflow](https://user-images.githubusercontent.com/26598127/54739505-bfe76c00-4bfb-11e9-94fc-e65eb4f8e7f3.jpg)
## 웹 크롤러

아동용 문화 컨텐츠를 수집하는 웹 크롤러  
Selenium으로 동적인 웹사이트도 수집 가능  
[레포지토리](https://github.com/anomie7/withKid-web-crawler)

## 인증 서버

사용자 인증 후 jwt를 발급(refresh, access)  
access token의 유효성을 검사 후 재발급(형식, 만료일시)  
refresh token을 갱신/재발급  
[인증 서버 레포지토리](https://github.com/anomie7/withkid-auth-server)

## api 서버

컨텐츠 검색(페이징 가능)  
콘텐츠 캐싱(레디스)  
사용자 로그 저장(레디스)  
[레포지토리](https://github.com/anomie7/withKid-api-server)  
## ULOG 서버
스토리지는 Firebase의 Firestore 사용  
유저의 검색 조건 저장  
유저의 이벤트 로그 저장  
전체 이벤트의 조회수 저장  
서비스에 접속한 당일 이전의 7일간 가장 많이 검색한 지역과 카테고리를 반환하는 기능('전체' 조건은 제외)  
[레포지토리](https://github.com/anomie7/withKid-ulog-server)  
## 웹 서버(nginx)

### 정적 자원 서버  
spa를 제공  
이미지 제공  

### 로드밸런서  
letsencrypt의 ssl 인증서로 https 도입  
reverse proxy로 인증 서버와 리소스 서버에 해당하는 docker service를 매핑
## 인프라 관리(Docker)
개발 환경과 배포 환경의 일치와 CI, CD를 용이하게 하기 위해 도입  
  
인증 서버와 api 서버의 빌드한 jar 파일을 image로 배포  
생성한 이미지는 docker-compose.yml 파일로 한번에 실행  
간편한 컨테이너 관리와 확장을 위해 docker swarm 도입  
[docker hub](https://hub.docker.com/u/minudev1212/)  
[레포지토리](https://github.com/anomie7/withkid-dockerFile)  

## 부하 테스트

ngrinder을 docker를 이용하여 실행  
redis, resource-server, nginx 모두 vuser 100으로 3분간 실행했으나 서버 다운은 없었음.  
