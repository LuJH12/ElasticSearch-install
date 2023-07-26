# ElasticSearch-install-in-Ubuntu
解决问题：ElasticSearch如何在Ubuntu里安装，以及如何通过内网访问。

# ElasticSearch 在Ubuntu中部署
## ElasticSearch的下载及安装
根据[官网](https://www.elastic.co/guide/en/elasticsearch/reference/8.9/deb.html#deb-repo)的方法进行安装，这里的`8.9.0`代表elasticsearch的版本，有安装的其他版本的可以自行更改
```
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-8.9.0-amd64.deb
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-8.9.0-amd64.deb.sha512
shasum -a 512 -c elasticsearch-8.9.0-amd64.deb.sha512 
sudo dpkg -i elasticsearch-8.9.0-amd64.deb
```
## ElasticSearch 配置文件的修改
