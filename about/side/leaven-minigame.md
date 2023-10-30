---
description: 5개의 질문에 답하여 트위치 버츄얼 크루 '레븐' 멤버 중 나와 가장 잘 맞는 멤버를 찾는 미니게임
---

# 나와 가장 잘 맞는 레븐 멤버는? (2022.06)

## 개요

{% embed url="https://minigame.leaven.team" %}
웹사이트 (minigame.leaven.team)
{% endembed %}

{% embed url="https://github.com/dokdo2013/leaven-minigame" %}
GitHub (FE)
{% endembed %}

<figure><img src="../../.gitbook/assets/스크린샷 2023-10-30 18.37.56.png" alt=""><figcaption><p>메인 페이지</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/스크린샷 2023-10-30 18.38.22.png" alt=""><figcaption><p>문제 푸는 페이지</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/스크린샷 2023-10-30 18.42.07.png" alt=""><figcaption><p>결과 페이지</p></figcaption></figure>



## 기술스택

* Framework : Next.js
* UI Library : Daisy UI (Tailwind CSS)
* Error monitoring : Sentry
* 과거 배포 : Vercel
* 현재 배포 : 개인 쿠버네티스 클러스터 (SSG + Nginx)



## 주요 기능

* 5개의 질문에 답변을 하여 나와 가장 잘 맞는 레븐 멤버를 알 수 있는 미니게임
* 응답결과는 로컬스토리지에 저장되어 이전 번호로 돌아가서 응답값을 바꿀 수 있음
* 결과 페이지에서 '공유하기' 버튼을 누르면 결과 정보와 사이트 링크가 클립보드에 복사됨



## 세부 개발 과정

간단한 설문형 게임이나 유사 mbti 검사들이 netlify 등으로 배포되어 많은 호응을 얻고 있는 것에 착안해, 간단하게 질문형 미니게임을 만들어보고자 계획하였다. 기술적으로는 이전에 사용해본 적이 없던 Next.js와 Vercel을 통한 배포과정, 그리고 Tailwind CSS 기반의 Daisy UI를 적용하였다.

우선 질문과 답변을 만들고, 각 답변에 대한 멤버별 가중치를 설계하였다. (멤버별 MBTI 반영)

{% embed url="https://docs.google.com/document/d/1f6pWSB4MS_zczUiEzHbigZq6-sQQQyCFH4e7z5dVJ1E/edit?usp=sharing" %}

이후 최대한 빠르게 주요 기능을 개발하였다.



## 성장 포인트

* Next.js를 처음 사용해보았다. 기술이 궁금해서도 있지만 React를 사용할 때 라우팅 처리가 많이 복잡했어서, Next.js의 편리한 라우팅 기능을 사용해보고싶은 마음이 컸다.
* Tailwind CSS와 함께 Daisy UI를 처음 써봤다. 이후 Tailwind를 이용하는 프로젝트가 많아졌는데 이 때 좋은 경험을 받은 덕이 크다.
* 회사에서 Bugsnag을 사용하는 걸 보고 에러 모니터링 툴에 관심이 생겨 Sentry를 처음 도입해보았다.
* 배포를 위해 Vercel을 처음 사용해보았다. 대만족!
