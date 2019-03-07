# withkid-backend-structure
위드키드 백엔드 설명

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
[Swagger UI](https://:8081/swagger-ui.html#!/interpark-rest-controller/getEventUsingGET)  

## Docker Container

인증 서버와 api 서버의 빌드한 jar 파일을 image로 배포  
생성한 이미지는 docker-compose.yml 파일로 한번에 실행  
간편한 컨테이너 관리와 확장을 위해 docker swarm 도입  
개발 환경과 배포 환경의 일치  
CI, CD를 용이하게 하기 위함  
[docker hub](https://hub.docker.com/u/minudev1212/)  
[레포지토리](https://github.com/anomie7/withkid-dockerFile)  

## 부하 테스트

ngrinder을 docker를 이용하여 실행  
redis, resource-server, nginx 모두 vuser 100으로 3분간 실행했으나 서버 다운은 없었음.  
