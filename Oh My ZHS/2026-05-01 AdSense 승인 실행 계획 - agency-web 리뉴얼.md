---
title: "AdSense 승인 실행 계획: agency-web 기반 oh-my-zhs.com 리뉴얼"
date: 2026-05-01T10:03:08+09:00
status: review-required
tags:
  - adsense
  - oh-my-zhs
  - agency-web
  - execution-plan
  - zero-human-studio
source:
  - /Users/gabriel.k/Documents/Workspace/ohmyzhs/adsense-approval-benchmark-2026.md
repo: /Users/gabriel.k/Documents/Workspace/ohmyzhs/agency-web
primary_domain: oh-my-zhs.com
not_target:
  - auto-ops.lotiony.com
  - blog.oh-my-zhs.com 리뉴얼
---

# AdSense 승인 실행 계획: agency-web 기반 oh-my-zhs.com 리뉴얼

> 이 문서는 `adsense-approval-benchmark-2026.md` 브레인스토밍 문서를 실행 계획으로 정리한 것이다.  
> 검토 전까지는 `review-required` 상태이며, 코딩 착수 기준 문서로 쓰기 전에 Gabriel이 면밀히 검토해야 한다.

## 0. 중요한 정정

이 계획의 대상은 다음이다.

```text
/Users/gabriel.k/Documents/Workspace/ohmyzhs/agency-web
```

목표 사이트는 다음이다.

```text
oh-my-zhs.com
```

이 계획의 대상이 아닌 것:

```text
auto-ops.lotiony.com
blog.oh-my-zhs.com 리뉴얼
/Users/gabriel.k/Documents/Workspace/ohmyzhs/blog
```

`adsense-approval-benchmark-2026.md`는 브레인스토밍/벤치마크 문서다. 그 문서에는 과거 옵션으로 `tools.lotiony.com`, `opskit.lotiony.com`, `auto-ops.lotiony.com` 같은 후보가 언급되어 있지만, 현행 실행 계획의 중심은 `agency-web` 기반 `oh-my-zhs.com` 리뉴얼이다.

---

## 1. 목적

`oh-my-zhs.com`을 기존 agency/portfolio 느낌의 사이트에서 AdSense 승인 가능성이 높은 public utility + guide hub로 재구성한다.

기존 Zero Human Studio의 정체성은 완전히 버리는 것이 아니라, 다음처럼 재해석한다.

기존:

```text
AI-only agency / Zero Human Studio
```

현행 목표:

```text
AI-built practical tools studio
```

핵심은 “AI로 만든다” 자체가 아니라, 방문자가 즉시 사용할 수 있는 도구와 충분한 설명 콘텐츠를 제공하는 것이다.

---

## 2. 승인 전략 요약

AdSense 승인을 위해 순수 블로그보다 다음 구조를 우선한다.

```text
Tools + Guides + Templates + Trust Pages
```

목표는 다음이다.

- 공개적으로 즉시 사용 가능한 tool pages
- 각 tool page의 설명, 예시, FAQ, 관련 링크
- thin content가 아닌 guide pages
- About / Contact / Privacy / Terms / Disclaimer
- sitemap / robots / canonical / mobile UX / no broken links
- Google crawler가 접근 가능한 static 또는 SSR/SSG 페이지

---

## 3. 최종 사이트 방향

### 3.1 브랜드 방향

브랜드명은 기존 `oh-my-zhs.com` / Zero Human Studio 자산을 살린다.

가능한 표현:

```text
Oh My ZHS
Zero Human Studio
AI-built practical tools and guides
```

주의:

- “AI-only agency”라는 추상적 agency pitch가 전면에 오면 안 된다.
- fake-looking portfolio metrics, 과장된 agency claim, 추상적 service copy를 줄인다.
- 방문자는 사이트에 들어오자마자 “뭘 할 수 있는지” 알아야 한다.

### 3.2 1차 포지셔닝 문장 후보

아래는 후보이며 확정 전 검토가 필요하다.

1. `Useful tools and guides built through autonomous AI workflows.`
2. `Practical web tools, calculators, and guides from Zero Human Studio.`
3. `AI-built utilities for everyday work, automation, and Korean-local tasks.`

### 3.3 피해야 할 방향

- `auto-ops.lotiony.com`으로 새 사이트를 만든다는 방향
- blog repo를 리뉴얼 대상으로 삼는 방향
- 기존 4개 블로그 글을 중심 자산으로 삼는 방향
- Taro/Saju를 1차 승인 표면 전면에 배치하는 방향
- “100개 무료 툴” 같은 얇은 clone tool site 느낌

---

## 4. 대상 repo와 현황

작업 대상 repo:

```bash
cd /Users/gabriel.k/Documents/Workspace/ohmyzhs/agency-web
```

원격:

```text
https://github.com/ohmyzhs/agency-web.git
```

현재 알려진 stack:

- Next.js 16.2.2
- React 19.2.4
- Tailwind 4
- TypeScript
- ESLint

중요한 local instruction:

```text
/Users/gabriel.k/Documents/Workspace/ohmyzhs/agency-web/AGENTS.md
```

내용 요지:

```text
This is NOT the Next.js you know.
Next 16 문서를 확인하고 작업할 것.
```

따라서 구현 전에는 `node_modules/next/dist/docs/`의 관련 문서를 확인해야 한다.

---

## 5. 기존 자산 사용 방침

### 5.1 agency-web

`agency-web`를 1차 리뉴얼 베이스로 사용한다.

이유:

- 이미 Next.js app structure가 있다.
- 기존 `layout`, `sitemap`, `robots`, `privacy`, `contact` 등이 있다.
- `oh-my-zhs.com` 프론트 사이트 역할에 맞다.

단, 대폭 교체할 것:

- Home copy
- Services/Work 중심 IA
- 일반 agency landing 느낌
- fake-looking portfolio metrics
- generic SaaS gradient style
- emoji icon 중심 카드

### 5.2 blog repo

`/Users/gabriel.k/Documents/Workspace/ohmyzhs/blog`는 이 계획의 대상이 아니다.

기존 blog 글 4개는 승인 전략의 핵심 자산으로 보지 않는다. 필요하면 문장/아이디어만 참고하고, `agency-web` 안의 `/guides`에 새 콘텐츠를 작성한다.

### 5.3 unit-converter-ait

기존 unit converter는 참고 자산이다.

사용 방침:

- 코드 전체를 그대로 옮기기보다, unit/category logic과 UX 아이디어를 참고한다.
- `agency-web`에 맞는 web-first tool page로 새로 구현한다.
- Toss in-app mini app 맥락은 1차 AdSense 승인 표면에서 제거한다.

### 5.4 smart-todo-ait

1차 AdSense 승인 사이트의 핵심 도구로 쓰지 않는다.

후보:

- Phase 2 이후 productivity template/tool로 편입 가능
- 지금은 IA와 승인 표면을 흐리지 않도록 보류

### 5.5 Taro / Saju

Phase 2로 보류한다.

이유:

- AdSense 1차 승인 전에는 사이트 주제를 흐릴 수 있다.
- entertainment/culture experiment로 다루려면 disclaimer와 data handling 설명이 필요하다.
- medical/financial/legal/life-decision claim으로 오해될 여지를 피해야 한다.

---

## 6. 목표 IA

1차 리뉴얼에서 목표로 하는 public route:

```text
/
/tools
/tools/[slug]
/guides
/guides/[slug]
/templates
/about
/contact
/privacy
/terms
/disclaimer
/sitemap.xml
/robots.txt
```

검토 포인트:

- `/services`, `/work`를 유지할지 제거할지 결정 필요
- 유지한다면 AdSense 승인 전에는 전면 navigation에서 낮은 우선순위로 둔다
- empty category/tag/archive/search page를 만들지 않는다

---

## 7. MVP 도구 목록

### 7.1 Tier 1: Korea-friendly practical tools

우선순위 높음.

1. Pyeong Converter
   - 평 ↔ m²
   - 한국 부동산/공간 단위 설명

2. KST Timezone Converter
   - KST ↔ 주요 time zones
   - remote team / launch / handoff 용도

3. Korean Shoe Size Converter
   - Korean mm ↔ US/UK/EU/JP references
   - brand fit caveat

4. KRW Currency Calculator
   - 수동 환율 입력
   - fee/spread 설명
   - live quote 아님 명시

5. Cooking Measurement Converter
   - cup / tbsp / tsp / ml / grams
   - ingredient density caveat

6. Unit Converter
   - length / weight / volume / temperature / area
   - 기존 unit-converter-ait 참고 가능

### 7.2 Tier 2: AI / automation / developer tools

7. LLM Cost Calculator
   - input/output token 분리
   - requests/day
   - model price assumptions
   - cache/retry/growth caveat

8. Automation ROI Calculator
   - saved time
   - hourly value
   - build cost
   - maintenance
   - failure buffer

9. Cron Explainer
   - 5-field cron explanation
   - timezone caveat

10. JSON/YAML Validator
   - JSON format/error
   - YAML은 parser dependency 여부 결정 필요

11. Webhook Payload Formatter
   - JSON pretty-print
   - event/id/timestamp/signature field extraction

### 7.3 Tier 3: micro utilities

12. Text Case Converter
13. Slug Generator
14. UTM Builder
15. Markdown Table Generator
16. Timestamp Converter
17. Color Contrast Checker

Tier 3는 빠르게 만들 수 있지만, 각 tool page가 thin page로 보이지 않도록 설명/FAQ/예시를 붙인다.

---

## 8. 콘텐츠 목표

AdSense 신청 전 목표:

- Tool pages: 최소 12개, 가능하면 17개
- Guides: 최소 20개, 안정권은 30개 이상
- Templates/checklists: 5개 이상
- Policy/trust pages: 5개

총 indexable useful pages 목표:

```text
최소 40개
안정권 50~60개
```

---

## 9. Guide 후보

### 9.1 Korea-friendly tools guides

1. 평수와 제곱미터를 헷갈리지 않게 변환하는 법
2. 한국 아파트 면적 표기를 읽는 법
3. KST를 해외 시간대와 맞추는 법
4. 해외 신발 사이즈를 한국 사이즈로 읽는 법
5. 환율 계산기를 쓸 때 자주 틀리는 지점
6. 요리 계량 단위를 컵·스푼·그램으로 바꾸는 기준

### 9.2 AI / automation guides

7. LLM API 비용 계산 전 확인할 토큰 개념
8. 자동화 ROI를 계산할 때 포함해야 하는 비용
9. Cron 표현식을 사람이 읽을 수 있게 해석하는 법
10. Webhook payload를 디버깅하는 기본 절차
11. JSON과 YAML 설정 파일을 검증하는 실무 체크리스트
12. 자동화 실패 비용을 계산하는 법
13. AI agent workflow를 운영할 때 필요한 체크리스트
14. 반복 작업을 자동화할지 판단하는 기준

### 9.3 Utility UX / practical web guides

15. 유용한 변환기 UX를 설계하는 법
16. Copy button이 utility tool에서 중요한 이유
17. Markdown 표를 깨지지 않게 만드는 법
18. UTM 링크를 만들 때 캠페인 이름을 정리하는 법
19. Timestamp를 seconds와 milliseconds로 구분하는 법
20. 색상 대비를 배포 전에 확인해야 하는 이유
21. 모바일 utility page 체크리스트
22. 도구 페이지를 thin content로 보이지 않게 만드는 법

추가 8개 이상은 도구 구현 후 실제 사용 사례에서 파생한다.

---

## 10. Templates / checklists 후보

1. Automation ROI worksheet
2. LLM cost estimation worksheet
3. Webhook debugging checklist
4. Launch QA checklist
5. Tool page content checklist
6. AdSense readiness checklist
7. Internal link checklist

---

## 11. Tool page 품질 기준

각 tool page는 다음 요소를 가져야 한다.

- 즉시 사용 가능한 UI
- 모바일에서 44px 이상 tap target
- example/preset
- clear error state
- result explanation
- method/formula 설명
- common mistakes
- FAQ
- related tools
- related guides
- unique title/description/canonical metadata
- crawler가 읽을 수 있는 정적 설명 콘텐츠

광고 배치 주의:

- input field 바로 옆 금지
- primary action button 바로 옆 금지
- copy/download/result action 주변 금지
- 사용자가 실수로 광고를 클릭할 수 있는 위치 금지

---

## 12. 필수 trust/policy pages

### About

포함할 것:

- Zero Human Studio / Oh My ZHS 소개
- AI-built practical tools studio라는 현재 방향
- 도구와 가이드를 만드는 기준
- 사람이 검토/운영한다는 책임 소재 표현

피할 것:

- “사람이 전혀 없다”를 무책임하게 보이게 하는 문장
- 과장된 agency 성과/수치

### Contact

포함할 것:

- 실제 연락 방법
- 응답 기대치
- bug report / correction / business inquiry 구분 가능하면 좋음

### Privacy

포함할 것:

- 기본 analytics/cookies
- tool input이 서버로 저장되는지 여부
- contact form data 처리
- future ad/AdSense cookie disclosure

### Terms

포함할 것:

- 도구 결과는 참고용
- 오류 가능성
- 사용자의 책임
- 서비스 변경 가능성

### Disclaimer

포함할 것:

- 계산기/변환기/자동화 추정치는 참고용
- financial/legal/medical/professional advice 아님
- 환율/비용/시간 계산의 한계

---

## 13. 디자인 계획

브레인스토밍 문서의 방향:

1. 브랜드 아이콘부터 새로 잡는다.
2. Claude Design 방식으로 화면/UX 시안을 만든다.
3. 선택된 방향을 `DESIGN.md`에 고정한다.
4. 그 뒤 implementation agent가 DESIGN.md를 기준으로 구현한다.

### 13.1 DESIGN.md에 포함할 항목

- Brand principles
- Color tokens
- Typography tokens
- Spacing/radius/shadow tokens
- Layout rules
- Component rules
- Tool page UX rules
- Guide/article page rules
- Accessibility baseline
- Do/don't examples

### 13.2 브랜드 아이콘 시안 후보

브레인스토밍 문서의 후보:

1. ZHS Monogram Grid
2. Empty Cursor
3. Hollow Studio Mark

산출물:

- favicon
- app icon 512x512
- header logo
- OG image mark
- SVG 원본

### 13.3 핵심 화면 시안

최소 3개 화면:

1. Home
2. Tool detail page
3. Guides index / article page

각 화면은 최소 3안:

- Conservative
- Strong-fit
- Divergent

---

## 14. 실행 순서

### Phase 0. 정정과 기준 고정

- [ ] 이 문서 검토 및 수정
- [ ] 이 문서를 현재 작업의 canonical plan으로 승인할지 결정
- [ ] `adsense-approval-benchmark-2026.md`는 brainstorming/reference로만 취급
- [ ] `auto-ops.lotiony.com`을 현재 범위에서 제외
- [ ] `/Users/gabriel.k/Documents/Workspace/ohmyzhs/blog`를 현재 범위에서 제외

### Phase 1. 안전한 repo 시작

- [ ] `agency-web` 현재 상태 확인
- [ ] `AGENTS.md` 확인
- [ ] Next 16 local docs 확인
- [ ] `main` 최신 상태 확인
- [ ] 새 브랜치 생성

권장 브랜치명:

```bash
restructure/adsense-tools-hub
```

명령:

```bash
cd /Users/gabriel.k/Documents/Workspace/ohmyzhs/agency-web
git checkout main
git pull --ff-only
git checkout -b restructure/adsense-tools-hub
```

### Phase 2. 현재 사이트 백업/캡처

- [ ] 기존 home/about/services/work/contact/privacy 상태 기록
- [ ] 현재 sitemap/robots 확인
- [ ] 주요 파일 목록 기록
- [ ] 가능하면 local dev server screenshot 저장
- [ ] 현재 상태를 `.hermes/baseline/` 또는 `docs/baseline/`에 정리

### Phase 3. 디자인/IA 확정

- [ ] `DESIGN.md` 초안 작성
- [ ] Brand icon 3안
- [ ] Home / Tool detail / Guide page 시안
- [ ] 라우팅 확정
- [ ] `/services`, `/work` 처리 방침 확정

### Phase 4. Foundation 구현

- [ ] `src/lib/tools.ts` registry
- [ ] `src/lib/guides.ts` registry
- [ ] `src/lib/templates.ts` registry
- [ ] `ToolCard`
- [ ] `ToolPageShell`
- [ ] `GuideCard`
- [ ] `GuidePageShell`
- [ ] `/tools`
- [ ] `/tools/[slug]`
- [ ] `/guides`
- [ ] `/guides/[slug]`
- [ ] `/templates`
- [ ] metadata/canonical 구조

### Phase 5. Policy/trust pages

- [ ] About rewrite
- [ ] Contact confirm/update
- [ ] Privacy update
- [ ] Terms create/update
- [ ] Disclaimer create/update
- [ ] footer에 policy links 노출

### Phase 6. Tier 1 tools

- [ ] Pyeong Converter
- [ ] KST Timezone Converter
- [ ] Korean Shoe Size Converter
- [ ] KRW Currency Calculator
- [ ] Cooking Measurement Converter
- [ ] Unit Converter

### Phase 7. Tier 2 tools

- [ ] LLM Cost Calculator
- [ ] Automation ROI Calculator
- [ ] Cron Explainer
- [ ] JSON/YAML Validator
- [ ] Webhook Payload Formatter

### Phase 8. Tier 3 micro utilities

- [ ] Text Case Converter
- [ ] Slug Generator
- [ ] UTM Builder
- [ ] Markdown Table Generator
- [ ] Timestamp Converter
- [ ] Color Contrast Checker

### Phase 9. Content layer

- [ ] 12개 guide draft
- [ ] 20개 guide draft
- [ ] 30개 guide target
- [ ] 5개 templates/checklists
- [ ] 모든 tool page에서 related guide 연결
- [ ] 모든 guide에서 related tool 연결

### Phase 10. Technical SEO / AdSense QA

- [ ] sitemap includes all public routes
- [ ] robots allows crawling
- [ ] no accidental noindex
- [ ] canonical domain correct for `oh-my-zhs.com`
- [ ] broken links check
- [ ] mobile UX smoke test
- [ ] no placeholder/lorem/empty categories
- [ ] policy pages complete
- [ ] Search Console 준비
- [ ] AdSense 신청 전 checklist 완료

---

## 15. 커밋 전략

각 phase는 작은 단위로 커밋한다.

권장 커밋 예시:

```text
docs: add adsense restructure execution plan
docs: add design system draft
feat: restructure navigation for tools hub
feat: add tools registry and shell
feat: add korea-friendly converters
feat: add automation calculators
feat: add developer utility tools
feat: add micro utility tools
feat: add policy pages for adsense readiness
feat: add guide registry and initial guides
seo: update sitemap and robots for tools hub
```

주의:

- `main` 직접 작업 금지
- 큰 변경 전 브랜치 확인
- repo 확인 없이 코드 수정 금지
- `blog` repo로 이동하지 말 것

---

## 16. 검증 명령

기본 검증:

```bash
pnpm lint
pnpm build
```

추가 검증 후보:

```bash
pnpm dev
```

브라우저 QA:

- Home
- Tools index
- Tool detail
- Guides index
- Guide article
- About
- Contact
- Privacy
- Terms
- Disclaimer
- Mobile viewport

---

## 17. AdSense 신청 전 완료 조건

최소 조건:

- [ ] 12개 이상 working public tool pages
- [ ] 20개 이상 guide/template/content pages
- [ ] About / Contact / Privacy / Terms / Disclaimer 완료
- [ ] sitemap / robots 정상
- [ ] 주요 public pages Google index 가능
- [ ] 모바일 UX 문제 없음
- [ ] broken links 없음
- [ ] placeholder/lorem/fake stats 없음
- [ ] Taro/Saju 전면 노출 없음
- [ ] 광고 배치 계획이 accidental click 정책을 위반하지 않음

안정권:

- [ ] 17개 working tools
- [ ] 30개 이상 guide pages
- [ ] 5개 templates/checklists
- [ ] Search Console에서 주요 page 색인 확인
- [ ] 2~6주 정도의 사이트 운영/색인 기간

---

## 18. 이번 실수 방지 규칙

작업 시작 전 반드시 확인:

```bash
pwd
git rev-parse --show-toplevel
git status --short --branch
git remote -v
```

정답이어야 하는 값:

```text
repo: /Users/gabriel.k/Documents/Workspace/ohmyzhs/agency-web
remote: https://github.com/ohmyzhs/agency-web.git
```

잘못된 값:

```text
/Users/gabriel.k/Documents/Workspace/ohmyzhs/blog
https://github.com/ohmyzhs/blog.git
```

현재 계획에서 금지:

- `auto-ops.lotiony.com`을 목표 도메인으로 가정하기
- `blog` repo에서 Auto-Ops/Oh My ZHS 리뉴얼 작업하기
- 과거 메모리의 폐기된 안을 현재 목표보다 우선하기
- brainstorming 문서를 canonical execution plan처럼 직접 실행하기

---

## 19. 다음 첫 액션

Gabriel 검토 후, 승인되면 첫 작업은 이것이다.

```bash
cd /Users/gabriel.k/Documents/Workspace/ohmyzhs/agency-web
git status --short --branch
git checkout main
git pull --ff-only
git checkout -b restructure/adsense-tools-hub
```

그 다음:

1. 현재 사이트 상태 백업
2. `DESIGN.md` 초안 작성
3. IA 확정
4. tool/guides/templates registry 설계

---

## 20. 검토 필요 질문

Gabriel이 확인해야 할 것:

1. 사이트 이름을 `Oh My ZHS`로 갈지, `Zero Human Studio`를 전면에 둘지?
2. `/services`와 `/work`를 삭제할지, 낮은 우선순위로 유지할지?
3. 1차 승인 전 언어는 영어 중심, 한국어 중심, bilingual 중 무엇으로 갈지?
4. Tool pages의 1차 우선순위는 Korea-friendly tools부터가 맞는지?
5. Guides는 영어로 작성할지, 한국어로 작성할지?
6. `DESIGN.md`를 먼저 만들고 구현할지, IA/foundation을 먼저 만들고 디자인을 붙일지?
7. 기존 `unit-converter-ait`에서 어떤 로직만 참고할지?

---

## 21. 결론

이 계획의 핵심은 다음이다.

```text
agency-web을 기반으로 oh-my-zhs.com을 AdSense 승인 가능한 tools + guides hub로 리뉴얼한다.
```

브레인스토밍 문서에서 나온 과거 도메인 후보나 blog repo 작업은 현재 실행 범위가 아니다.

이 문서는 실행 전 검토용 canonical plan 후보이며, Gabriel의 확인 후 실제 작업 계획으로 고정한다.
