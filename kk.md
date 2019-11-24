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
