## 2. limits.conf 설정 변경 
```
$ sudo vim /etc/security/limits.conf
```

i 키보드 입력(insert mode)
```
*       hard    nofile  65536
*       soft    nofile  65536
*       soft    nproc   4096
*       hard    nproc   4096
```
esc 키보드 입력
:wq! 키보드 입력 후 enter

## 3. sysctl.conf 설정 변경 
```
$ sudo vim /etc/sysctl.conf
```

i 키보드 입력

vm.max_map_count=262144

esc 키보드 입력
:wq! 키보드 입력 후 enter

## 4. Reboot EC2 instance 
```
$ sudo reboot
```


도커 설치

amazon-linux-extras enable docker
amazon-linux-extras install docker -y

도커컴포즈
sudo curl -L "https://github.com/docker/compose/releases/download/1.24.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

sudo chmod +x /usr/local/bin/docker-compose

sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
