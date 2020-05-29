# Scaling to 100K Users [link](https://alexpareto.com/scalability/systems/2020/02/03/scaling-100k.html)

以Graminsta为例，看从side project到scalable，是否有迹可循。

## 1 user - 本地部署
Client, API 和 Database都在同一台机器上。
- client: app or website
- Database: persist data
- API: serves requests for and around data


## 10 user - 分离database layer
使用Amazon's RDS或Digital Ocean这一类的Managed Database。这比self-hosting在单机或EC2 instance要expensive一些，但有很多可以直接用的add-on能解决不少问题。
- multi-region redundancy
- read replicas
- automated backups, etc
![image: 10 users](images/10k-user-img1.png)


## 100 user - 分离 client layer
拆分实体是构建scalable app的关键所在。如果系统的某一部分获得了更高的流量，则需要把它拆分出来，根据它的traffic特点来handle scaling the service.
这里拆分client层的原因：因为有不同的客户端（mobile、web等）都在consume同一api


## 1,000 user - 加 load balancer

## 10,000 user - CDN

## 100,000 users - scaling data layer 

