# Docker
## Docker는 무엇인가?
컨테이너를 빌드, 배포, 실행, 업데이트, 관리할 수 있는 오픈 소스 플랫폼입니다.

## Docker commands
`docker ps`

`docker ps -a`

`docker stop (container name) `

`docker images`

`docker rmi`

`docker run`

you can also append a command

ex. docker run ubuntu sleep 5


`docker run (app):(tag)`

ex. docker run redis:4.0

`docker run -p (docker portnumber):(app portnumber) (app)`

ex. docker run -p 80:5000 mysql

`docker run -v (host directory):(docker portnumber) (app)`


`docker pull`

`docker attach`

`docker dettach`

`docker inspect`

`docker logs (app name)`

`docker build`

### docker exec vs docker attach vs docker run -i

run -it : 새로운 컨테이너를 생성해 실행하는 명령어

exec : container에서 새로운 프로세스를 실행시킬 때 사용한다

attach : attach는 실행되고 있는 container에 접속할 때 사용합니다.

### Dockerfile
1. OS 로 시작
2. (Instruction) (Argument) 구조 이는 layer라고 불린다.
ex. FROM Ubuntu
	RUN apt-get update
	ENTRYPOINT FLASK_APP=/opt/source-code/app.py