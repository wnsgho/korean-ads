# First-Time User Guide

처음 사용하는 사용자가 광고 관리자 화면을 열고 로그인만 하면 Codex가 읽기 전용으로 확인할 수 있도록 안내하는 가이드다. 사용자가 어떤 플랫폼을 써야 하는지 모르면 먼저 `platform-login-router.md`로 보낼 플랫폼을 고른다.

## User Promise

사용자에게 먼저 이렇게 설명한다.

```text
제가 광고 계정을 직접 수정하지는 않습니다. 아래 링크 중 사용하는 플랫폼을 열고 직접 로그인해 주세요. 로그인 후 캠페인/광고 성과 화면이 보이면 "로그인 완료"라고 알려주세요. 그러면 화면에 보이는 지표만 읽기 전용으로 확인해서 진단 요약을 만들겠습니다.
```

## Platform Login Links

사용자에게 필요한 링크만 보여준다. 여러 플랫폼을 한 번에 다 열게 하지 말고, `platform-login-router.md`에 따라 가장 중요한 1-2개부터 시작한다.

| Platform | Link | First page to open after login |
|---|---|---|
| Google Ads | [https://ads.google.com/](https://ads.google.com/) | Campaigns |
| Meta Ads Manager | [https://adsmanager.facebook.com/](https://adsmanager.facebook.com/) | Campaigns |
| Naver Search Ads | [https://searchad.naver.com/](https://searchad.naver.com/) or [http://manage.searchad.naver.com](http://manage.searchad.naver.com) | 광고관리 or 캠페인/키워드 성과 |
| Kakao Business | [https://business.kakao.com/](https://business.kakao.com/) | 카카오모먼트 캠페인 |
| Coupang Ads | [https://ads.coupang.com/](https://ads.coupang.com/) | 광고관리 or 상품별 성과 |
| Daangn Business | [https://business.daangn.com/](https://business.daangn.com/) | 광고 관리 or 캠페인 성과 |

## Beginner Flow

1. Ask which platform they want to diagnose first.
2. Send only the matching official link.
3. Ask the user to log in themselves.
4. Ask them to navigate to the campaign or performance table.
5. Ask them to confirm:
   - "로그인 완료"
   - "성과 화면 열림"
   - desired date range, usually last 30 days
6. Use browser-assisted collection in read-only mode.
7. Report what was visible and what still requires CSV export.

## Copy-Paste Prompts For The User

Simple:

```text
네이버 검색광고를 먼저 진단하고 싶어요. 로그인 링크를 알려주고, 제가 로그인 완료라고 말하면 브라우저로 읽기 전용 확인해서 요약해 주세요.
```

Multi-platform:

```text
Google Ads, Meta, 네이버를 같이 보고 싶어요. 우선 Google Ads부터 링크를 열어 로그인하겠습니다. 로그인 후 캠페인 화면이 보이면 읽기 전용으로 확인해 주세요.
```

Agency:

```text
클라이언트 광고 계정을 봐야 합니다. 제가 로그인된 화면을 열어둘 테니 계정명, 캠페인명, 성과 지표만 읽고 광고주용 요약 보고서를 만들어 주세요. 개인정보나 결제정보는 보지 말아주세요.
```

## What To Say Before Browser Access

브라우저 조작 전에 짧게 확인한다.

```text
확인 범위는 읽기 전용입니다. 보이는 성과표, 캠페인 상태, 추적 경고만 확인하고 예산/입찰/ON-OFF/저장/게시 버튼은 누르지 않겠습니다.
```

## If The User Gets Stuck

Login issue:

```text
제가 비밀번호나 인증번호를 대신 입력하면 안 됩니다. 로그인은 직접 완료해 주세요. 로그인 후 성과 화면이 보이면 다시 알려주세요.
```

Google unsafe browser warning:

```text
Google이 자동화된 로그인 화면을 안전하지 않은 브라우저로 판단해 차단한 상태입니다. 이 화면에서는 계속 시도하지 말고, 평소 사용하는 Chrome에서 https://ads.google.com/aw/campaigns 를 직접 열어 로그인해 주세요. 계정 선택 후 캠페인 화면이 보이면 "로그인 완료"라고 알려주세요. 그러면 열린 탭을 읽기 전용으로 확인하겠습니다.
```

Wrong account:

```text
현재 화면이 원하는 광고 계정인지 계정명만 확인해 주세요. 다른 계정으로 이동해야 하면 이동 후 "준비됨"이라고 알려주세요.
```

No campaign data visible:

```text
현재 화면에서는 성과표가 보이지 않습니다. 캠페인/광고관리/성과 메뉴로 이동하거나 CSV 내보내기 파일을 주시면 이어서 진단하겠습니다.
```

Blocked automation:

```text
플랫폼이 브라우저 자동 확인을 막는 것 같습니다. 이 경우 화면 캡처나 CSV export로 전환하면 같은 방식으로 진단할 수 있습니다.
```

## Test Script For Skillathon Demo

Use this if no real ad account is available.

```text
처음 사용하는 사용자라고 가정하고 Google Ads와 네이버 검색광고 중 어디부터 로그인하면 되는지 안내해 주세요. 사용자가 로그인 완료라고 말하면 어떤 화면과 지표를 읽기 전용으로 확인할지 단계별로 설명해 주세요.
```
