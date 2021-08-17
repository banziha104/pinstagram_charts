# Pinstagram Charts

> Google Cloud Platform, Kubernetes, Helm 을 이용한 DevOps 프로젝트 


## Pinstagram 프로젝트

- [📱 Pinstagram Android (Kotlin & AndroidX)](https://github.com/banziha104/pinstagram_android)
- [🍃 Pinstagram WAS (Spring Boot)](https://github.com/banziha104/pinstagram-was)
- [🚚 Pinstagram DevOps (GKE & K8s & Helm)](https://github.com/banziha104/pinstagram_charts)
- [🕳 Pinstagram Socket (Node.js & Socket.io)](https://github.com/banziha104/pinstagram_socket)

## 개요 

| 구분                      | 서비스                                  | 비고             |
|-------------------------|--------------------------------------|----------------|
| Node 구성                 | 마스터 1대 + 슬래이브 2대                     | 공유 코어, 2GB RAM |
| Container               | Docker                               |                |
| Container Orchestration | Google Kubernetes Engine (GKE)       |                |
| Container Repository    | Google Container Registry (GCR)      |                |
| Load Balancer & Ingress | Google Global Static IP Name Ingress |                |
| [TLS 인증서](https://github.com/banziha104/pinstagram_charts/blob/master/templates/managed_sertificate.yml)             | Google ManagedCertificate            |                |
| DNS                     | Google ManagedCertificate            |                |
| Database                | Google SQL                           |                |

- 적용 예정 
    - Service Mash : istio (아직 GKE에서는 Beta)
    - Monitoring : Prometheus & Grafana(시각화)


## 전체 아키텍쳐

- ![architecture](https://github.com/banziha104/pinstagram_charts/blob/master/markdown/images/architecture.png)

## Features

- [Ingress](https://github.com/banziha104/pinstagram_charts/blob/master/markdown/01_Ingress.md)
- [Service](https://github.com/banziha104/pinstagram_charts/blob/master/markdown/images/02_Service.md) 
- [Deployment](https://github.com/banziha104/pinstagram_charts/blob/master/markdown/images/03_Deployment.md)

## Inpression

- 기존에 현업에서는 Spring Boot와 Stomp를 이용하여서 개발하였었는데, 이번에 최대한 가볍게 만들어보고자 Node.js를 활용해보았습니다.
- 충분히 적은량의 코드로도 퍼포먼스를 낼 수 있어서 좋았습니다.
- 다만 현재는 한개의 이벤트를 이용하고 있어 문제가 안되지만, 조금 소켓의 영향이 커진다면 TypeScript로 엄격하게 검사할 필요가 있어보입니다.