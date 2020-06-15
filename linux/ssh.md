# ubuntu ssh 설치

서버용 pc로 ssh 접속이 안됨
/etc/ssh/sshd_config에 port 22로 지정되었음  
확인해보니 ssh 서버가 설치가 안됐음 (ssh 클라이언트는 기본적으로 설치됨)

1. ssh 설치 확인
```sh
dpkg --list | grep ssh
```


2. openssh-server 설치
```sh
sudo apt-get install ssh
```


3. port 지정 (ssh서버 설치하니까 port 22 지정이 풀렸음)


4. ssh 재시작
```sh
sudo service ssh restart
```


참고
http://programmingskills.net/archives/315  
https://stackoverflow.com/questions/47079224/how-do-i-check-if-openssh-is-installed-on-ubuntu
