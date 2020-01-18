# eureka

# docker eureka IP 显示 172.0.0.2

```shell
eureka:
  instance:
    prefer-ip-address: true
    instance-id: 192.168.15.195:8000  --- 用于显示正常IP
  client:
    service-url:
      defaultZone: http://192.168.15.168:8761/eureka

spring:
  application:
    name: Client
  cloud:
    inetutils:
      preferredNetworks:
      - 192.168
      - 10.0
```

```shell
docker run --rm --name tomcat8000 \
-p 8000:8000 \
-v /data01/docker/tomcat/tomcat8000/webapps:/usr/local/tomcat/webapps \
-v /data01/docker/tomcat/tomcat8000/conf:/usr/local/tomcat/conf \
-e "eureka.instance.ip-address=192.168.15.195" -e "eureka.instance.prefer-ip-address=true" \
-d tomcat:8.5
```
