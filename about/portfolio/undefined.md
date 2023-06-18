---
description: 모바일 기반 직업카드 심리검사 플랫폼
---

# 직업카드심리검사

## 개요

{% embed url="https://jobcard.jobmap.kr" %}
jobcard.jobmap.kr
{% endembed %}

* 기간 : 2020년 5월 1일 \~ 2020년 8월 31일
* 회사 : 미래직업전망연구원
* 담당 범위 : 유지보수 (Backend, Frontend)



## 주요 기술 스택

### Frontend

* Bootstrap + jQuery

### Backend & Infrastructure

* ASP.Net (C#), MSSQL
* 카페24 윈도우호스팅 환경에서 서비스 (기존 : Azure)

### Android Application

* 자바로 개발된 안드로이드 하이브리드 앱
* 로그인/로그아웃, 햄버거 메뉴만 네이티브로 구현하고 이외의 부분은 웹뷰로 처리해서 서버와 통신



## 상세 개발 내용

* 버그픽스, 서버 모니터링 등 유지보수
* 어드민 페이지 신규 기능 추가 및 일부 페이지 디자인, 로직 수정

<figure><img src="../../.gitbook/assets/Untitled (6).png" alt=""><figcaption><p>메인 페이지</p></figcaption></figure>

인수인계 받기 전에는 Azure에서 운영 중이던 프로젝트였습니다. 하지만 운영비 절감과 관리의 용이성때문에 카페24 윈도우 호스팅으로 이전한 뒤 인수인계를 받았습니다. C# 언어 자체는 그렇게 어렵지 않았으나, 닷넷과 MSSQL이 처음이라 구조를 파악하고 익히는데 1\~2주정도 시간이 소요되었습니다.

인수인계 후 특정 상황에서 서버가 계속 죽는 문제를 발견해 해결하였습니다. (자세한 내용은 아래에)

심리검사 특성상 이용자로부터 설문 데이터를 받아서 로직에 의해 결과가 도출되게 되는데, 해당 로직의 변경사항이 있어 이를 반영하고, 특정 상황에서 잘못된 결과가 나오는 버그를 수정하였습니다. 또한 일부 페이지에서 디자인 변경, 기능 수정 등 일반적인 유지보수 작업을 진행했습니다.

검사 중간에 페이지를 이탈할 경우 검사 결과가 이상하게 나오는 오류가 일부 보고되어, 어드민 페이지에서 특정 이용자의 검사 결과를 초기화하고 다시 검사를 시행할 수 있도록 하는 기능을 추가하였습니다.



## 주요 개발 이슈 및 해결 사례

### 1) 여러 명이 동시에 접속할 경우 간헐적으로 서버가 죽는 문제 발

*   **문제 발견**

    테스트 과정에서는 별 문제가 없었으나, 여러 명이 동시에 접속하여 테스트를 진행할 경우 간헐적으로 서버가 죽는 문제가 발생하였습니다.
*   **원인 확인**

    첫 메인 랜딩 페이지는 정상적으로 접속되는 것에 반해 DB 커넥션이 필요한 페이지가 작동하지 않는 것으로 보아 DB쪽 문제임을 먼저 확인하였습니다. 이에 에러 메세지 설정을 켜고 오류를 확인, 커넥션 풀이 꽉 차서 연결이 되지 않는 오류 메세지를 발견하였습니다. 이어서 DB쪽에서 connection 관련 모니터링을 하려 했으나 카페24 호스팅을 사용하는 특성상 권한이 부족해 대부분의 모니터링 기능을 사용할 수 없었습니다.
*   **임시 조치**

    당시에는 Connection Pool 관련 지식이 없어서 해결방법을 찾는데까지 시간이 좀 걸릴 것이라 판단했습니다. 따라서 Connection Pool 관련 오류임을 확인하고 원격에서 Connection Pool을 초기화할 수 있도록 링크를 만들어서, 해당 링크로 접속하면 `SqlConnection.ClearAllPools();` 구문이 실행되도록 해놓고, 해결책을 찾기 전까지 모니터링을 하며 문제 발생시마다 풀을 초기화시켜줬습니다.
*   **문제 해결**

    심리 검사의 문항 각각에 답변할 때마다 DB Update가 이뤄지는 구조인데, 150개 문항으로 문항 수가 많아서 잦은 연결이 이뤄질 수밖에 없습니다. 다만 호스팅 특성상 DB 서버의 설정을 변경할 수가 없기에 코드 레벨에서 문제를 해결해야 했고, 테스트를 거쳐 Connection Pool이 주는 성능상의 이점을 포기함에도 불구하고 큰 성능 저하가 발생하지 않아 연결문에 `Pooling=false` 를 넣어 사용하지 않는 방향으로 문제를 해결했습니다.

### 2) 카페24 호스팅 트래픽 초과 알림 개발

이용할 트래픽에 따라 요금제가 정해지고, 해당 트래픽을 모두 소진하면 사이트 접속이 당일 자정까지 차단되는 호스팅의 특성상 이용 트래픽에 대한 관리가 필요했습니다. 아쉽게도 트래픽 알림 기능은 따로 존재하지 않았고, 결제 카드를 연결해두면 자동 초기화도 가능했으나 선택적으로 초기화가 필요할 때에만 초기화를 하고 싶었기에 트래픽 모니터링 코드를 파이썬으로 간단하게 작성하여 활용했습니다.

{% embed url="https://github.com/dokdo2013/cafe24_traffic_monitoring" %}
dokdo2013/cafe24\_traffic\_monitoring
{% endembed %}



## 성장

* 닷넷과 C# 관련 지식을 얻게 되었습니다. 닷넷으로 개발된 웹사이트의 구조를 이해하게 되었습니다.
* MSSQL을 운용할 수 있게 되었습니다. 특히 이 프로젝트에는 Stored Procedure가 많이 이용되었는데, 프로시저의 개념을 알고 어떤 형태로 사용되는지 알게 되었습니다. 트러블슈팅을 하며 Connection Pool에 대해서도 알게 되었습니다.