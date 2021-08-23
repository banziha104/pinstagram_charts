# Pinstagram Charts

> Google Cloud Platform, Kubernetes, Helm 을 이용한 DevOps 프로젝트

<br>
## 목차 

### [1.Pinstagram 프로젝트](#Pinstagram-프로젝트)
### [2.개요](#개요)
### [3.주요 구현 사항](#주요-구현-사항)
### [4.전체 아키텍쳐](#전체-아키텍쳐)
### [5.기술부채](#기술부채)
### [6.후기](#후기)


<br>

## Pinstagram 프로젝트

> 전체 서비스 설명은  [Android](https://github.com/banziha104/pinstagram_android)에 명시되어 있습니다

- ### 기획 배경
  - 새로운 기술을 도입해야 될 때마다 새로운 토이프로젝트를 만들었는데(그러다보니 레파지토리가 250개를 넘었습니다..), 이렇게 계속 진행하다보니 다른 기술들과 유기적으로 연결되지 못하는 느낌을 받았습니다.
  - 이를 개선하고자 하나의 토이 프로젝트를 만들고, 이를 지속적으로 개선해나가는 것이 좋겠다고 판단하여 시작한 프로젝트입니다.
- ### 서비스 내용
  - 기획 내용은 단순히 특정한 위치에 사진을 올리고, 이를 볼 수 있는 서비스입니다.
  - 개발자가 처음으로 하는 프로젝트인 헬로우월드, 그리고 그 다음으로 많이하는 계산기, 그리고 그와 쌍두마차를 이루는 기본적인 게시판 어플의 확장 버전입니다.
- ### 개인적인 규약
  - Git Submodule 미활용 : WAS와 Android의 경우 각 모듈별로 git submodule에 등록하는게 효율적이지만, 레파지토리가 너무 많아지면 관리가 안될 것 같아서 통합된 Git으로 관리합니다.
  - 기획 디자인 최소화 : 개발적인 프로젝트이기 때문에 사업성, 당위성 등은 최대한 배제하고 개발하기에 깔끔한 기획과 디자인만 가져갑니다. 그렇기 때문에 기획 디자인적으로 뜬금없는 페이지(예: Talk)가 들어갈 수 있습니다
  - 기술부채 : 한시적으로 끝나는 프로젝트가 아닌, 지속적인 프로젝트임으로, 현재 가능한 기술을 사용하고, 볼륨 및 러닝커브로 못 가져간 기술은 천천히 도입할 예정입니다.
- ### 서비스 주요 기능
  - Home : 특정 위치에서 1KM 반경내에 있는 데이터들을 그리드뷰 형식으로 보여줍니다
  - Map : 특정 위치에서 1KM 반경내에 있는 데이터들을 지도 형식으로 보여줍니다.
  - Talk : Socket 통신을 이용한 메세지입니다. 위치기반으로 하는 지역톡 개념이아닌 서비스 이용자 전체와 소통합니다.
  - Write : 특정 위치에 게시물을 명시할 수 있습니다.
  - Auth : 로그인, 로그아웃, 회원가입 등을 진행할 수 있습니다.

- ### 프로젝트 목록
  - ### [📱 Pinstagram Android (Kotlin & AndroidX)](https://github.com/banziha104/pinstagram_android)
  - ### [🍃 Pinstagram WAS (Spring Boot)](https://github.com/banziha104/pinstagram-was)
  - ### [🚚 Pinstagram DevOps (GKE & K8s & Helm)](https://github.com/banziha104/pinstagram_charts)
  - ### [🕳 Pinstagram Socket (Node.js & Socket.io)](https://github.com/banziha104/pinstagram_socket)

  

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
| DNS                     | Google Cloud DNS                     | 가비아와 연동      |
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


## License

```
MIT License

Copyright (c) 2021 Coguri

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
