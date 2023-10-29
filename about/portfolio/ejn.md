---
description: 필요에 따라 개발한 사내 프로덕트
---

# EJN 사내 프로덕트 개발

## 사내 슬랙봇 개발 (2023.07)

<figure><img src="../../.gitbook/assets/스크린샷 2023-10-29 21.35.45.png" alt=""><figcaption><p>Slack에 공유</p></figcaption></figure>

* 주요 기능
  * TWIP 개발서버 캐시 충전, 트위치 유저 조회, 사무실 에어컨 조종, CloudFront Cache invalidate 등 다양한 유틸리티 기능 제공
  * 슬랙 ID 기반 기능별 권한 제어 (ex. 개발자만 Cache invalidate 가능)
  * 모든 요청에 대해 Google Drive 스프레드시트에 Audit log 기록
* 개발 배경 : 기존에 파이썬 슬랙봇이 있었는데 개발했던 직원 퇴사 후 관리도 되지 않고 있고 기능도 제한적이어서, 현재 회사 기술스택에 맞춰 NestJS로 신규 개발 진행.
* 개발 기간 : 2일 (주말)
* 사용 기술 : NestJS, Google Drive API, Ngrok
* 특이 사항 : 문서화도 함께 진행하여 다른 개발자들도 쉽게 기여할 수 있고, 실제로 쓰고 싶은 기능을 만들어 PR로 올려주기도 하였음. 로컬 개발시에는 Ngrok을 적극 활용하여 슬랙 연동을 하였음.



## EJN GPT (2023.03)

<figure><img src="../../.gitbook/assets/스크린샷 2023-10-29 21.42.33.png" alt=""><figcaption><p>EJN GPT 메인</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/스크린샷 2023-03-26 12.24.14.png" alt=""><figcaption><p>EJN GPT 내부 화면</p></figcaption></figure>

* 주요 기능 : OpenAI와 여러 생성형 AI 제공 업체의 API를 통해 여러 AI 모델들을 사용해볼 수 있음.
* 개발 배경 : ChatGPT Plus를 유료 결제해서 사용하는 직원들이 평상시 사용하는 만큼을 API 호출로 사용한다면 $20 가격 대비 훨씬 저렴하게 이용할 수 있다는 점에 착안, 공통 API 키로 사용하면 전체적으로 비용을 아낄 수 있을 것 같아서 개발하였음.
* 개발 기간 : 1일
* 사용 기술 : Next.js, Chakra UI, NestJS, Cloudflare Pages, Cloudflare Access
* 특이 사항 : Cloudflare Pages에 배포하여 따로 CI/CD 파이프라인을 구축하지 않아도 자동으로 배포가 되고, Cloudflare Access를 이용하여 회사 직원들만 구글 계정으로 인증하여 들어와서 사용할 수 있음 (접근제어)



## EJN Meal (2022.10)

<figure><img src="../../.gitbook/assets/스크린샷 2023-10-29 21.51.09.png" alt=""><figcaption><p>슬랙에 공유한 내용 (함께 개발한 FE개발자 분이 올려주셨다)</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (11).png" alt=""><figcaption><p>서비스 캡쳐 화면</p></figcaption></figure>

* 주요 기능 : 회사 위치(삼성동) 근처의 배달 음식점을 웹상에서 검색해서 보여주고, 음식점별 메뉴와 가격까지 볼 수 있음
* 개발 배경 : 원래 예전에 있던 개발자분이 배민API를 우회해서 웹상에서 배민 음식점을 검색하고 메뉴를 볼 수 있는 웹페이지를 만들어주셨는데, 퇴사하신 이후에도 잘 쓰다가 어느 순간 접속이 안 되어 빠르게 대체 서비스를 만들어보았습니다.
* 개발 기간 : 11시간
* 담당 분야 : Frontend 일부, Backend API 전체
* 사용 기술 : Next.js, Mantine UI, NestJS
* 내부 구조 : 공개되어 있는 비공식 요기요 API를 우회하여 요기요 음식점 기준으로 데이터 표시. 현재는 요기요가 Cloudflare를 적용하여 서버에서 호출하면 봇 체크가 떠서 사용하지 못하는 중
