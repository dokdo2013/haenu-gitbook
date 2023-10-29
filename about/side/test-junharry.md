---
description: 트위치 스트리머 '전해리' 방송 1주년 기념 퀴즈 응시 웹사이트
---

# 해리배치고사 (2022.07)

## 개요

{% embed url="https://test.junharry.com" %}
서비스 (test.junharry.com)
{% endembed %}

{% embed url="https://api-v1.leaven.team/docs#/%ED%95%B4%EB%A6%AC%EB%B0%B0%EC%B9%98%EA%B3%A0%EC%82%AC" %}
Swagger (api-v1.leaven.team)
{% endembed %}

{% embed url="https://github.com/dokdo2013/junharry-test-next" %}
GitHub (FE)
{% endembed %}

<figure><img src="../../.gitbook/assets/스크린샷 2023-10-30 00.03.10.png" alt=""><figcaption><p>로그인 시 화면</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/스크린샷 2023-10-30 00.03.42.png" alt=""><figcaption><p>테스트 응시 페이지</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/스크린샷 2023-10-30 00.07.52.png" alt=""><figcaption><p>해리배치고사 API Swagger 캡쳐</p></figcaption></figure>



## 기술 스택

### Frontend

* Next.js
* Chakra UI

### Backend

* FastAPI
* MariaDB (AWS RDS)
* Redis (AWS ElastiCache)



## 주요 기능 <a href="#user-content" id="user-content"></a>

* 트위치 로그인
* 테스트 응시와 결과 보기
* 주요 정책
  * 테스트 응시 전, 응시 후에는 테스트 페이지로 진입 불가
  * 테스트 응시 후에만 결과 페이지로 진입 가능
  * 응시 데이터를 기반으로 부정행위 여부 분석 가능
* 응시결과는 관리자페이지에서만 조회 가능



## 성장 포인트

* Next.js로 API를 연동하는 앱을 처음 만들어보았다 (SSR에 대한 이해가 부족해 막히는 부분이 좀 있었다)
* Twitch OAuth 연동을 FastAPI로 처음 해보았다! (짱신기)
* Redis를 처음 사이드 프로젝트에 도입했다 → 응답결과를 계산해서 DB에서 내려보내줄 때 사람이 몰리면 부하가 걸릴 수 있을 것 같아서 도입했는데.. 사실 이 정도 규모에선 필요가 없긴 하다
