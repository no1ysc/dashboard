# Mapping using Kibana
```
GET _cat/indices

DELETE myfile
```

```
PUT myfile
{
  "mappings": {
    "properties": {
      "Country": {
        "type": "keyword"
      },
      "Item Type": {
        "type": "keyword"
      },
      "Order Date": {
        "type": "date",
        "format": "M/d/yyyy"
      },
      "Order ID": {
        "type": "integer"
      },
      "Order Priority": {
        "type": "keyword"
      },
      "Region": {
        "type": "keyword"
      },
      "Sales Channel": {
        "type": "keyword"
      },
      "Total Cost": {
        "type": "float"
      },
      "Total Profit": {
        "type": "float"
      },
      "Total Revenue": {
        "type": "float"
      },
      "Unit Cost": {
        "type": "float"
      },
      "Unit Price": {
        "type": "float"
      },
      "Units Sold": {
        "type": "integer"
      }
    }
  }
}
```

```
GET myfile/_search
GET myfile/_mapping
```


# logstash - conf
```
$ vim file.conf
```
```
input {
  file {
    path => "/home/ec2-user/dashboard/data/5000_Sales_Records.csv"
    start_position => "beginning"
    #sincedb_path => "/dev/null" #only for develop
  }
}

filter {
  csv {
    separator => ","
    autodetect_column_names => true
  }
  date {
    match => ["Ship Date", "M/d/YYYY", "ISO8601"]
    timezone => "Asia/Seoul"
    target => "Ship Date"
  }
  mutate {
    remove_field => ["@version", "message", "path"]
  }
}

output {
  elasticsearch {
    hosts => ["본인주소입력:9200"]
    index => "myfile"
  }
  #stdout { }  #only for develop
}
```

```
$ bin/logstash -f file.conf
```

# scripted field
```
doc['Ship Date'].value.dayOfYear - doc['Order Date'].value.dayOfYear
```
```
(doc['Ship Date'].value.toEpochSecond() - doc['Order Date'].value.toEpochSecond()) / 60 / 60 / 24
```
