---
description: 개인 쿠버네티스 클러스터를 운영하며 얻은 경험을 공유합니다.
---

# ⚓ 개인 쿠버네티스 클러스터를 향한 여정

기존에 많은 개인 프로젝트를 배포하기 위해 여러 방법들을 사용해 왔습니다. EC2, Lightsail, Vercel, Cloudflare Pages 등... 여러 군데로 배포가 나뉘면서 관리에 어려움이 컸고, 비용도 상당히 많이 들어가서 효율적으로 관리하고자 하는 니즈가 많이 있었습니다.

이전에도 여러 차례 쿠버네티스로 개인 클러스터를 만들고 거기에 모든 앱을 옮기려는 시도들을 해왔습니다. 하지만 쉽게 하지 못했는데, 1차 시도인 EKS는 비용 문제로, 2차 시도인 GKE는 러닝커브 문제로 결국 성공하지 못했습니다. 한 때는 Dockerize 조차 어려워했지만, 꾸준히 쿠버네티스와 DevOps 분야에 대해 공부를 지속한 결과 Vultr와 함께 개인 클러스터를 배포할 수 있게 되었습니다.

Vultr Kubernetes Engine은 한국에서 거의 알려지지 않은 Managed Kubernetes Service입니다. 최대 장점은 비용인데요, 저렴한 인스턴스 비용과 함께 마스터 노드 비용을 받지 않는다는 특징을 가지고 있습니다. 자잘하게 LB나 Block Storage 등 제약조건이 있는 부분이 있긴 하지만, 테스트해봤을 때 특별한 이슈가 없어 본격적으로 기존 앱들을 옮기기 시작했습니다.



## 기본 구조

* Cluster : Vultr Kubernetes Engine (VKE)
* Container Registry : Docker Hub
* CI : Github Actions
* CD : ArgoCD
* Monitoring : Grafana, Loki & Promtail, Prometheus
* Ingress : Nginx Ingress Controller
* Secret Management : Selaed Secret

## GitOps Repository

{% embed url="https://github.com/dokdo2013/haenu-cluster" %}
