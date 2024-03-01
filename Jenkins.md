# Jenkins
## Jenkins는 무엇인가?
젠킨스는 소프트웨어 개발 시 **지속적으로 통합 서비스**를 제공하는 툴이다. **CI(Continuous Integration) 툴** 이라고 표현한다. Git 과 같은 버전관리시스템과 연동하여 소스의 **커밋을 감지하면 자동적으로 자동화 테스트가 포함된 빌드**가 작동되도록 설정할 수 있다.


## 설치 방법 (Centos)
`sudo yum install epel-release -y`

`sudo yum install java-11-openjdk -y`

`sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo --no-check-certificate`

`sudo rpm --import http://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key`

`sudo yum install jenkins -y`

Edit /lib/systemd/system/jenkins.service file and change Jenkins port to 8090 by updating Environment="JENKINS_PORT=" variable value.

`sudo vi /lib/systemd/system/jenkins.service`

Once done start Jenkins service.

`sudo systemctl start jenkins`

you can find initial admin password under

/var/lib/jenkins/secrets/initialAdminPassword

## SSH키 등록하기
/home/user/.ssh 다이렉토리에서 ssh key 확인 젠킨스 ui에 paste
vps나 aws ec2이면 프라이빗키 입력

ssh socket 찾기

`curl -Lv http://localhost:8085/login 2>&1 | grep -i 'x-ssh-endpoint`

Jenkins SSH server connection

`mike@jenkins-server:~$ ssh -i /home/mike/.ssh/jenkins_key -l mike -p 8022 jenkins-server help`

-i flag is used to point to mike's private SSH key. Remember, we have already added the public key in the Jenkins configuration.
-l is the login user which in our example is mike
-p is the port which we found out in the previous step to be 8022

## Jenkins restart
`sudo systemctl restart jenkins`

## Jenkins backup

primary files to back up : $JENKINS_HOME 와 jobs

이 JENKINS_HOME에는 configurations files
jobs폴더에는 ci, cd등의 pipeline 파일들이 있다.

추천하는 backup plugins 은 thinbackup
thinbackup에서는 backup directory를 설정해 주어야 한다.
backup directory를 설정할때 policy에 따른 chmod를 설정해줘야 한다.

## Jenkinsfiles
pipeline을 효율적으로 제어하기 위한 파일
Jekinsfiles 구조는
Build Agent -> Stages -> Steps로 구성

Jenkinsfile (Declarative Pipeline)
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}



## ETC
Cli command lists :
https://www.jenkins.io/doc/book/managing/cli/