---
description: 트위치 스트리머 '전해리'의 방송일정/공지사항을 보여주기 위한 웹사이트
---

# 전해리 방송일정 (2022.06)

## 개요

{% embed url="https://junharry.com" %}
서비스 (junharry.com)
{% endembed %}

{% embed url="https://api-v1.leaven.team/docs#/%EC%A0%84%ED%95%B4%EB%A6%AC%20%EB%B0%A9%EC%86%A1%EC%9D%BC%EC%A0%95" %}
Swagger (api-v1.leaven.team)
{% endembed %}

{% embed url="https://github.com/dokdo2013/junharry" %}
GitHub (FE)
{% endembed %}

<figure><img src="../../.gitbook/assets/스크린샷 2023-10-30 00.22.19.png" alt=""><figcaption><p>메인 페이지 (아프리카 이적 후)</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/스크린샷 2023-10-30 00.06.22.png" alt=""><figcaption><p>어드민 페이지 로그인</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/스크린샷 2023-10-30 00.06.41.png" alt=""><figcaption><p>어드민 - 일정 관리 페이지</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/스크린샷 2023-10-30 00.06.52.png" alt=""><figcaption><p>어드민 - 공지사항 관리 페이지</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/스크린샷 2023-10-30 00.26.56.png" alt=""><figcaption><p>Swagger 명세 캡쳐</p></figcaption></figure>



## 기술 스택

### Frontend

* React.js (CRA)
* Ant Design (Web)
* Chakra UI (Admin)

### Backend

* FastAPI
* MariaDB (AWS RDS)
* Redis (AWS ElastiCache)



## 주요 기능 <a href="#user-content" id="user-content"></a>

* 메인 페이지
  * (구버전) Ant Design 캘린더 기능을 이용해서 캘린더 형식으로 일정을 보여줬음
  * (신버전) 아프리카 이적 이후 Ant Design 카드를 이용해서 공지사항을 보여줌
* 어드민 페이지
  * 로그인 : ID/PW 방식, JWT 기반 인증 (로컬스토리지에 저장)
  * 일정 등록/관리, 공지 등록 등 기능
  * 해리배치고사 결과 열람도 여기서 가능
  * 위지윅에디터로 TinyMCE 사용



## 성장 포인트

Ant Design을 처음 이용해봤다. 깔끔하긴 한데... 검색하면 중국어밖에 안 나와서 TroubleShooting할 때 애로사항이 있었다.
