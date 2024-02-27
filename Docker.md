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


`docker run:(tag)`

ex. docker run redis:4.0

`docker pull`

`docker attach`

`docker dettach`

### docker exec vs docker attach vs docker run -i

run -i : 새로운 컨테이너를 생성해 실행하는 명령어

exec : 실행 중인 컨테이너에 명령어를 전달(외부 -> 내부)

attach : 실행 중인 컨테이너에 직접 들어가 명령어를 실행 (내부 접근)