# Setup Apache Zeppelin 0.10.0 as a single user on Ubunthu 22.04
Official web-site: [https://zeppelin.apache.org/](https://zeppelin.apache.org/)

## Installlation

1) Install Java:
```
sudo apt install openjdk-18-jre-headless
```
2) Download binnary package
```
wget https://dlcdn.apache.org/zeppelin/zeppelin-0.10.1/zeppelin-0.10.1-bin-all.tgz
```
3) Extract archive
```
tar -zxf zeppelin-0.10.1-bin-all.tgz
```

4) cp template configuration file to actual one:
```
cp conf/zeppelin-site.xml.template conf/zeppelin-site.xml
```

5) Change binding adress in ```conf/zeppelin-site.xml``` to ```0.0.0.0``` to allow remote access:
```
<property>
  <name>zeppelin.server.addr</name>
  <value>0.0.0.0</value>
  <description>Server binding address</description>
</property>
```

## Starting Apache Zeppelin
Run
```
bin/zeppelin-daemon.sh start
```
Zeppelin server is available on port ```8080``` by default

To stop Zeppelin:
```
bin/zeppelin-daemon.sh stop
```
