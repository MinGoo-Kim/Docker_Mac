# Docker_Mac

##### 다운로드 Docker Toolbox (Docker Machine을 포함하고 있다)
- https://www.docker.com/toolbox

##### 설치 확인
- `docker version`

##### docker-machine의 목록
- `docker-machine ls`

##### 머신 정보
- `docker-machine inspect 머신명`

##### Docker Machine을 사용하여 virtualbox를 드라이브로하는 VM을 추가
- `docker-machine create --driver virtualbox 머신명`

##### 머신을 실행
- `docker-machine start 머신명` 

##### Docker Machine의 환경을 설정
- `docker-machine env 머신명`

##### 실제 docker에 접속하기 위한 shell을 실행(위에서 env로 만든 설정파일을 환경변수로 설정하는 것이다)
- `eval "$(docker-machine env 머신명)" `

##### docker의 이미지 목록
- `docker images`

##### docker 컨테이너 실행 (이 명령어를 실행한 이후 docker는 로컬에 이미지가 없다면 hub에서 이미지를 찾아서 pull한 뒤 실행을 할 것이다 - 이미지 다운로드)
- `docker run ubuntu:16.04`
- `docker run --rm -it ubuntu:16.04 /bin/bash`
- `docker run -d -p 1234:6379 redis`
- `docker run -d -p 3306:3306 \
  -e MYSQL_ALLOW_EMPTY_PASSWORD=true \
  --name mysql \
  mysql:5.7`
- `docker run -d -p 8080:80 \
  --link mysql:mysql \
  -e WORDPRESS_DB_HOST=mysql \
  -e WORDPRESS_DB_NAME=wp \
  -e WORDPRESS_DB_USER=wp \
  -e WORDPRESS_DB_PASSWORD=wp \
  wordpress`
- `docker run -d -p 8888:8888 -p 6006:6006 teamlab/pydata-tensorflow:0.1`

##### 컨테이너 목록
- `docker ps -a`

##### 컨테이너 중지
- `docker stop ${CONTAINER_ID}`

##### 컨테이너 제거
- `docker rm ${CONTAINER_ID}`

##### 이미지 다운로드 (pull은 최신버전으로 다시 다운)
- `docker pull ubuntu:14.04`

##### 이미지 제거
- `docker rmi ${IMAGE_ID}`

##### 컨테이너 로그 보기
- `docker logs --tail 10 ${CONTAINER_ID}` 마지막 로그 10줄
- `docker logs -f ${CONTAINER_ID}` 실시간 로그

##### 컨테이너 명령어 실행
- `docker exec -it mysql /bin/bash` run은 새로 컨테이너를 만들어서 실행, exec는 실행중인 컨테이너에 명령어를 내림
- `docker exec -it mysql mysql -uroot`

##### docker-compose.yml 파일을 이용
- `docker-compose up`

참조
--------
- https://subicura.com/2017/01/19/docker-guide-for-beginners-1.html
- https://subicura.com/2017/01/19/docker-guide-for-beginners-2.html
- https://subicura.com/2017/02/10/docker-guide-for-beginners-create-image-and-deploy.html
