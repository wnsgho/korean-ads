# Korea Ads Auditor

비개발자 광고주와 마케터를 위한 한국형 퍼포먼스 광고 진단 Codex Skill입니다.

## Why

기존 광고 감사 스킬은 글로벌 플랫폼 중심이라 한국 현장에서 자주 쓰는 네이버, 카카오, 쿠팡, 당근 광고의 운영 맥락을 충분히 반영하기 어렵습니다. 동시에 한국 광고주도 Google, YouTube, Meta를 매우 자주 운영하므로, 이 스킬은 글로벌 플랫폼과 국내 플랫폼이 섞인 계정을 함께 진단합니다. CSV, 스크린샷, 붙여넣은 지표, 사용자가 이미 로그인한 광고 관리자 화면을 기반으로 예산 누수, 추적 문제, 플랫폼별 역할 충돌, 컴플라이언스 리스크를 빠르게 정리합니다.

## What It Covers

- Google Ads, YouTube Ads, Meta Ads
- 네이버 검색광고, 쇼핑검색광고, 파워링크
- 카카오모먼트, 비즈보드, 카카오톡 채널 광고
- 쿠팡 상품광고, 매출 최적화 광고, AI 스마트 광고
- 당근 비즈니스 로컬 광고
- 한국 광고주가 함께 쓰는 Google Ads, Meta Ads
- Codex 브라우저를 통한 로그인된 관리자 화면 읽기 전용 확인
- 처음 사용하는 사용자를 위한 플랫폼 로그인 링크 안내
- 표시광고, 후기/체험단, 개인정보/맞춤형 광고 리스크

## Files

```text
korea-ads-auditor/
├── SKILL.md
├── README.md
├── references/
│   ├── platform-checklists.md
│   ├── platform-login-router.md
│   ├── first-time-user-guide.md
│   ├── browser-assisted-collection.md
│   ├── compliance-and-privacy.md
│   └── report-template.md
└── evals/
    └── evals.json
```

## Demo Prompt

```text
월 500만원을 네이버 검색광고와 쿠팡 광고에 쓰는 생활용품 스마트스토어입니다.
네이버는 클릭은 많은데 구매가 적고, 쿠팡은 ROAS가 250% 정도입니다.
제공 가능한 데이터는 네이버 키워드 리포트와 쿠팡 상품별 광고 성과 CSV입니다.
광고주에게 보낼 수 있는 진단 요약과 7일 액션 플랜을 만들어주세요.
```

## Expected Output

- 한국 광고 건강 점수
- 플랫폼별 핵심 문제
- 즉시 조치 5개
- 7일 액션 플랜
- 추가로 필요한 데이터
- 광고주에게 보낼 수 있는 요약문

## Browser-Assisted Mode

API 키 없이도 사용자가 이미 로그인한 광고 관리자 화면을 Codex 브라우저로 읽기 전용 확인할 수 있습니다.

원칙:

- 로그인은 사용자가 직접 수행
- 비밀번호, 2FA, 결제정보 저장 금지
- 기본은 읽기 전용
- 예산, 입찰, 캠페인 ON/OFF, 저장 버튼 클릭 금지
- 자동화가 막히면 CSV 또는 스크린샷으로 전환

처음 쓰는 사람용 예시:

```text
처음 사용합니다. 네이버 검색광고를 진단하고 싶어요.
로그인 링크를 알려주고, 제가 로그인 완료라고 말하면 읽기 전용으로 화면을 확인해서 요약해 주세요.
```

플랫폼을 모를 때:

```text
어디에 로그인해야 하는지 모르겠습니다. 제가 하는 광고 유형을 물어보고 맞는 로그인 링크를 골라주세요.
```

지원 링크:

- Google Ads: https://ads.google.com/
- Meta Ads Manager: https://adsmanager.facebook.com/
- Naver Search Ads: https://searchad.naver.com/
- Kakao Business: https://business.kakao.com/
- Coupang Ads: https://ads.coupang.com/
- Daangn Business: https://business.daangn.com/

## 1-Hour Skillathon Scope

이번 버전은 원본 claude-ads와 같은 방향으로 API 연동 없이 실무자가 바로 쓸 수 있는 진단 워크플로우에 집중했습니다. 대신 처음 쓰는 사용자를 위한 로그인 링크 안내와 Codex 브라우저로 로그인된 화면을 읽기 전용 확인할 수 있는 절차를 추가했습니다. 다음 버전에서는 Google Ads MCP, 네이버 SearchAd API, Kakao Moment API, CSV 파서, 리포트 PDF 생성까지 확장할 수 있습니다.
