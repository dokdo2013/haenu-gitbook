---
description: 2주만에 출시한 오픈소스 기반 핀볼게임 후원
---

# TWIP 핀볼게임

## 개요

{% embed url="https://pinball.twip.kr" %}
pinball.twip.kr
{% endembed %}

<figure><img src="../../.gitbook/assets/트윕 핀볼.gif" alt=""><figcaption><p>TWIP 핀볼게임 플레이영상</p></figcaption></figure>

후원액수에 따라 핀볼 구조물 내에 구슬을 만들고, 시작을 누르면 구슬이 떨어지며 가장 먼저 결승선을 통과한 구슬이 1등을 차지하는 웹 게임

* 기간 : 2023년 8월 3일 \~ 2023년 8월 18일
* 회사 : 이제이엔
* 담당 범위 : 전체



## 주요 기술 스택

### Frontend

* Next.js
* Chakra UI
* Socket.io



## 상세 개발 과정

### 프로젝트 진행 과정

프로젝트를 처음 시작한 계기는 직원분들과 점심시간에 아프리카TV에서 유행하고 있는 '핀볼게임'이라는 컨텐츠를 이야기하다가, 그걸 가져와서 후원시스템을 붙여보면 재밌겠다고 아이디어가 떠올랐습니다.

그래서 퇴근 이후 저녁시간을 들여 이틀정도만에 빠르게 PoC 수준의 제품을 만들고 사내에 공유했습니다.

<figure><img src="../../.gitbook/assets/스크린샷 2023-10-29 17.43.12.png" alt=""><figcaption><p>첫 PoC 수준의 제품 공유</p></figcaption></figure>

반응이 꽤 괜찮았고, 그 다음 주에 이틀정도 작업할 수 있는 시간을 받아서 피드백을 반영하고, 공개 가능한 수준까지 완성도를 끌어올렸습니다.

이후 내부 검토 과정과 홍보물 준비 과정을 거쳐 최초 공유 2주만인 8월 18일에 제품을 출시했습니다! :tada:

{% embed url="https://www.cast.help/update/twip-pinball" %}
홍보 게시물 (유튜브 쇼츠 + 홍보채널 게시물 + SNS)
{% endembed %}

### 개발 과정

> 원본 게임 레포 : [https://github.com/lazygyu/roulette](https://github.com/lazygyu/roulette)

MIT 라이센스 오픈소스 게임을 바탕으로, 기존 HTML + Typescript 구조를 Next.js 기반으로 포팅하고, Chakra UI로 디자인을 씌우고, 트위치 로그인을 붙여서 내부 API 호출을 통해 스트리머의 토큰을 받아올 수 있도록 구성했습니다.

이를 통해 스트리머는 한 번의 트위치 로그인만 거치면, 자동으로 후원금이 구슬로 생성되는 모습을 볼 수 있게 되었습니다.



## 성과

* 따로 프로모션이나 이벤트를 진행하지 않았음에도 출시 첫 달 핀볼게임을 통한 **후원액 500만원**을 달성했습니다.
* 아무런 기획도 없이 아이디어를 가볍게 구현해보고, 이를 제품화시켜 출시까지 해본 재미난 경험이었습니다. 투입한 리소스 대비 효율이 좋았고, 앞으로 꾸준히 맵 추가나 기능 개선 등이 이뤄진다면 지속적으로 매출을 발생시킬 수 있을 것으로 예상합니다.
