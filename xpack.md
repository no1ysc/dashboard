# Elasticsearch
## 1. Elasticsearch 내리기 
```
$ sudo docker-compose down elasticsearch
```

## 2. 보안기능 활성화
```
docker-compose.yml 내 environment 셋팅
```

## 3. Elasticsearch 시작
```
$ sudo docker-compose up -d elasticsearch
```

## 4. Password 생성
```
# elasticsearch docker에 접속
$ sudo docker exec -it elasticsearch /bin/bash 
```
```
# Password 생성
$ bin/elasticsearch-setup-passwords auto
# 화면에 출력되는 비밀번호 저장
```

# Kibana
## 1. Kibana 내리기
```
$ sudo docker-compose down kibana
```

## 2. Elasticsearch 접속 계정 설정
```
docker-compose.yml 내 environment 셋팅
```

## 3. Kibana 시작
```
$ sudo docker-compose up -d kibana
```
