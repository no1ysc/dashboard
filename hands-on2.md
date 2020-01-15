# mapping using kibana
```
GET _cat/indices

DELETE myrdbms
PUT myrdbms
{
  "mappings": {
    "properties": {
      "age": {
        "type": "integer"
      },
      "cabin": {
        "type": "keyword"
      },
      "embarked": {
        "type": "keyword"
      },
      "fare": {
        "type": "float"
      },
      "name": {
        "type": "text"
      },
      "parch": {
        "type": "integer"
      },
      "passengerid": {
        "type": "integer"
      },
      "pclass": {
        "type": "keyword"
      },
      "sex": {
        "type": "keyword"
      },
      "sibsp": {
        "type": "integer"
      },
      "survived": {
        "type": "keyword"
      },
      "ticket": {
        "type": "keyword"
      }
    }
  }
}
```
```
GET myrdbms/_search
GET myrdbms/_mapping
```

# logstash - conf
```
$ vim rdbms.conf
```
```
input {
  jdbc {
    jdbc_validate_connection => true
    jdbc_connection_string => "jdbc:mysql://dashboard-8.cp7ovqbewwso.ap-northeast-2.rds.amazonaws.com:3306/fast"
    jdbc_user => "root"
    jdbc_password => "1q2w3e4r"
    jdbc_driver_library => "/home/ec2-user/dash10/data/mysql-connector-java-5.1.47.jar"
    jdbc_driver_class => "com.mysql.jdbc.Driver"
    statement => "SELECT * FROM titanic"
 }
}

output {
  elasticsearch {
    hosts => ["본인주소입력"]
    index => "myrdbms"
  }
  #stdout { }  #only for develop
}
```
```
$ bin/logstash -f rdbms.conf
```
