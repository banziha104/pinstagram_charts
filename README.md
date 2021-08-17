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
| [TLS 인증서]()             | Google ManagedCertificate            |                |
| DNS                     | Google ManagedCertificate            |                |
| Database                | Google SQL                           |                |

- 적용 예정 
    - Service Mash : istio (아직 GKE에서는 Beta)
    - Monitoring : Prometheus & Grafana(시각화)


## 전체 아키텍쳐

- ![architecture](https://github.com/banziha104/pinstagram_charts/blob/master/markdown/images/architecture.png)