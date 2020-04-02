## 젠킨스 란 ?

### CI (Continuous Integration)

- 빌드, 테스트 자동화
- 지속적 통합으로 모든 개발이 끝난 이후 코드 품질을 관리하는 방식의 단점을 해소 하기 위해 나타난 개념
- 개발중에 지속적으로 빌드와 테스트 진행
- 예를 들어 김밥을 만들어놓고 나서 김밥안에 재료들이 다 있는 지 확인하는 것 보다 처음부터 재료를 확인하면서 만드는 것이 더 유리한 것

### CD (Continuous Deploy / Delivery)

- 배포 자동화
- 소프트웨어가 항상 신뢰 가능한 수준에서 배포될 수 있도록 지속적 관리하자는 개념
- CI의 연장선으로 CI가 통과된 코드들을 서버에 배포하여 반영

---

## 환경

- OS (Ubuntu 18.04)

### 설치 전 환경 설정

1. 젠킨스를 사용 시 java 8 버전이 필요
```bash
    $ sudo apt update
    $ sudo apt install openjdk-8-jdk openjdk-8-jre
    $ java -version 
```
 2.  웹서버를 실행하기위한 Nginx 설치
```bash
    $ sudo apt-get install nginx
```
### 젠킨스 설치
```bash
    $ wget -q -O - https://pkg.jenkins.io/debian/jenkins-ci.org.key | sudo apt-key add -
```
GNU Wget은 HTTP 통신 또는 FTP 통신을 사용해 서버에서 파일 또는 콘텐츠를 다운로드할 때 사용하는 소프트웨어
```bash
    $ sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'

    $ sudo apt-get update
    $ sudo apt-get install jenkins
```
## Jenkins & Github

---

### Github 연동

1. Jenkins Server 접속
2. ssh key 생성 
```bash
        $ ps aux | grep jenkins        # 젠킨스 사용자 확인
        $ sudo -u jenkins /bin/bash    # 젠킨스 계정 사용
        $ mkdir /var/lib/jenkins/.ssh  # ssh-key 저장 디렉터리 생성
        $ cd /var/lib/jenkins/.ssh 
        $ ssh-keygen -t rsa 
```
3. Github 접속 
4. profile → Settings → Deploy Keys → Add Deploy Key
5. Deploy Key 생성
```bash
        # jenkins Server 
        # /var/lib/jenkins/.ssh
        $ cat id_rsa.pub
```
6. 5번에서 cat 명령어로 본 공개키를 Deploy Keys → Key 부분에 복붙!
7. Jenkins 접속
8. Credentials → Add Credentials
→ Kind `SSH Username With Private Key`
→ Username : 젠킨스 Job에서 보여줄 인증키 이름
→ Private Key : id_ras 개인 키 입력

## 도움 받은 글

[[QA] CI/CD 란?](https://itholic.github.io/qa-cicd/)

[Install Jenkins on Ubuntu 18.04 - Easy Step-by-Step Guide](https://www.hostinger.com/tutorials/how-to-install-jenkins-on-ubuntu/)