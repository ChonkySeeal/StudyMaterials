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

sudo systemctl start jenkins