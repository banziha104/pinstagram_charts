# Pinstagram Charts

> Google Cloud Platform, Kubernetes, Helm 을 이용한 DevOps 프로젝트

<br>

## Pinstagram 프로젝트

- ### [📱 Pinstagram Android (Kotlin & AndroidX)](https://github.com/banziha104/pinstagram_android)
- ### [🍃 Pinstagram WAS (Spring Boot)](https://github.com/banziha104/pinstagram-was)
- ### [🚚 Pinstagram DevOps (GKE & K8s & Helm)](https://github.com/banziha104/pinstagram_charts)
- ### [🕳 Pinstagram Socket (Node.js & Socket.io)](https://github.com/banziha104/pinstagram_socket)

<br>

## 목차 
 
### [1.개요](#개요)
### [2.주요 구현 사항](#주요-구현-사항) 
### [3.전체 아키텍쳐](#전체-아키텍쳐)
### [4.기술부채](#기술부채)
### [5.후기](#후기)


<br>

## 개요

| 구분                      | 서비스                                  | 비고             |
|-------------------------|--------------------------------------|----------------|
| Node 구성                 | 마스터 1대 + 슬래이브 2대                     | 공유 코어, 2GB RAM |
| Container               | Docker                               |                |
| Container Orchestration | Google Kubernetes Engine (GKE)       |                |
| Container Repository    | Google Container Registry (GCR)      |                |
| Load Balancer & Ingress | Google Global Static IP Name Ingress |                |
| [TLS 인증서](https://github.com/banziha104/pinstagram_charts/blob/master/templates/managed_sertificate.yml)             | Google ManagedCertificate            |                |
| DNS                     | Google Cloud DNS                     |                |
| Database                | Google SQL                           |                |
| Package Manager         | Helm                                 |                |
<br>

## 주요 구현 사항

- #### [Ingress](https://github.com/banziha104/pinstagram_charts/blob/master/markdown/01_Ingress.md)
- #### [Service](https://github.com/banziha104/pinstagram_charts/blob/master/markdown/images/02_Service.md)
- #### [Deployment](https://github.com/banziha104/pinstagram_charts/blob/master/markdown/images/03_Deployment.md)

<br>

## 전체 아키텍쳐

![architecture](https://github.com/banziha104/pinstagram_charts/blob/master/markdown/images/architecture.png)

<br>

## 기술부채

> 적용할 예정이 있는 부분입니다

- Develop
  - Scaffold : 단일 컨테이너로는 사용해보았는데, Helm과 연동방법을 아직 찾지 못해서 미뤄두었습니다.
- Production
  - CI/CD : Jenkins와 GCP Pipeline을 이용한 배포 자동화 (비용문제가..)
  - Service Mash : istio (아직 GKE에서는 Beta)
  - Monitoring : Prometheus & Grafana(시각화)

<br>

## 후기

- 평소에는 AWS를 이용하다 GCP를 이용해서 처음 개발해보았는데 생각보다 퍼포먼스가 나쁘지않습니다. 비용은 좀 비교해봐야 알 것 같습니다.
- k8s의 경우 어느한 값이 App Name 과 Selector 등 여러 군데에서 사용되고, 이를 변경하다보면 실수를 자주하게 되는데, Helm을 통해 변수화시켜서 굉장히 편했습니다.
