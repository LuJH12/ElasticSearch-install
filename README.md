# ElasticSearch-install-in-Ubuntu
解决问题：ElasticSearch如何在Ubuntu里安装，以及如何通过内网访问。

# ElasticSearch 在Ubuntu中部署
## ElasticSearch的下载及安装
根据[官网](https://www.elastic.co/guide/en/elasticsearch/reference/8.9/deb.html#deb-repo)的方法进行安装，这里的`8.9.0`代表elasticsearch的版本，有安装的其他版本的可以自行更改
```$
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-8.9.0-amd64.deb
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-8.9.0-amd64.deb.sha512
shasum -a 512 -c elasticsearch-8.9.0-amd64.deb.sha512 
sudo dpkg -i elasticsearch-8.9.0-amd64.deb
```

在安装完成后，需要配置一下ElasticSearch的启动方式
```$
sudo /bin/systemctl daemon-reload
sudo /bin/systemctl enable elasticsearch.service
```

之后，你就可以使用下列命令来启动或关闭ElasticSearch的进程了
```
sudo systemctl enable elasticsearch.service

sudo systemctl start elasticsearch.service

sudo systemctl stop elasticsearch.service
```

在启动ElasticSearch后，你可以测试下是否成功：
```
curl -X GET "localhost:9200/"
```
如果能成功返回类似于下列内容，就是成功了
```
{
  "name" : "user_name",
  "cluster_name" : "elasticsearch",
  "cluster_uuid" : "_8p9GX0JSKyNWkaKRLdNzw",
  "version" : {
    "number" : "8.8.2",
    "build_flavor" : "default",
    "build_type" : "deb",
    "build_hash" : "98e1271edf932a480e4262a47128sadee295ce6b",
    "build_date" : "2023-06-26T05:16:16.196344851Z",
    "build_snapshot" : false,
    "lucene_version" : "9.6.0",
    "minimum_wire_compatibility_version" : "7.17.0",
    "minimum_index_compatibility_version" : "7.0.0"
  },
  "tagline" : "You Know, for Search"
}
```
## ElasticSearch 配置文件的修改
