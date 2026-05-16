# Skillathon Submission

## Title

Korea Ads Auditor: 한국형 광고 계정 진단 자동화 스킬

## Problem

한국 광고주는 Google/Meta도 자주 쓰지만 그것만 쓰지는 않습니다. 네이버 검색광고, 카카오모먼트, 쿠팡 광고, 당근 광고가 함께 섞여 있고, 광고 데이터도 API보다 CSV, 스크린샷, 엑셀 요약, 로그인된 관리자 화면으로 공유되는 경우가 많습니다.

기존 글로벌 광고 감사 프롬프트는 한국 플랫폼의 운영 방식, 소상공인 맥락, 표시광고/후기광고/개인정보 리스크를 충분히 반영하지 못합니다.

## Solution

비개발자 마케터나 광고주가 지표를 붙여넣으면 Codex가 다음을 자동으로 정리합니다.

- 한국 광고 건강 점수
- Google/Meta와 네이버/카카오/쿠팡/당근 플랫폼별 문제
- Codex 브라우저 기반 로그인 화면 읽기 전용 확인
- 초보자용 로그인 링크 안내와 테스트 스크립트
- 사용자의 광고 유형에 따라 어떤 플랫폼에 로그인할지 고르는 라우터
- 즉시 조치할 예산 누수와 추적 이슈
- 표시광고, 체험단, 개인정보 리스크
- 광고주에게 보낼 수 있는 요약문
- 7일 액션 플랜

## Demo Prompt

```text
월 500만원을 네이버 검색광고와 쿠팡 광고에 쓰는 생활용품 스마트스토어입니다.
네이버는 클릭은 많은데 구매가 적고, 쿠팡은 ROAS가 250% 정도입니다.
제공 가능한 데이터는 네이버 키워드 리포트와 쿠팡 상품별 광고 성과 CSV입니다.
광고주에게 보낼 수 있는 진단 요약과 7일 액션 플랜을 만들어주세요.
```

## 1-Hour Build Scope

완성한 것:

- `SKILL.md`: 스킬 트리거, 워크플로우, 점수 체계, 출력 규칙
- `references/platform-checklists.md`: Google, Meta, 네이버, 카카오, 쿠팡, 당근 체크리스트
- `references/platform-login-router.md`: 어떤 광고 관리자에 로그인할지 고르는 라우터
- `references/first-time-user-guide.md`: 초보자용 로그인 링크와 진행 멘트
- `references/browser-assisted-collection.md`: 로그인된 광고 관리자 화면 읽기 전용 수집 절차
- `references/compliance-and-privacy.md`: 한국 광고/개인정보 리스크 체크
- `references/report-template.md`: 광고주용 보고서 템플릿
- `evals/evals.json`: 3개 현실형 테스트 프롬프트

의도적으로 제외한 것:

- 광고 계정 API 연동
- 자동 예산 변경
- 법률 자문
- PDF 리포트 생성

## Next Steps

- 네이버 SearchAd API, Kakao Moment API 연동
- 쿠팡/네이버 CSV 자동 파서
- 광고주용 PDF 보고서 생성
- 업종별 벤치마크 팩 추가
- 실제 광고 계정 샘플로 eval 확장

## Beginner Demo Script

```text
처음 사용합니다. 네이버 검색광고를 진단하고 싶어요.
로그인 링크를 알려주고, 제가 로그인 완료라고 말하면 읽기 전용으로 화면을 확인해서 요약해 주세요.
```

```text
어디에 로그인해야 하는지 모르겠습니다. 제가 하는 광고 유형을 물어보고 맞는 로그인 링크를 골라주세요.
```
