# jangbogi-handoff — 장보기 에이전트 전달면

「장보기」(주간 특가 식재료 → 저녁 5끼 → 실결제 장바구니 총액 최소화)가 만든 **장바구니 명세서**를 피클(Pickle)·dot(OpenAI dots) 같은 실행 에이전트에 넘기고, 담은 결과를 돌려받는 저장소다. 코드 없음, 문서만. 에이전트는 이 저장소를 읽고 쇼핑몰에 **담기만** 한다. **결제는 하지 않는다.**

## 에이전트가 읽는 순서
1. [AGENTS.md](AGENTS.md) — 모든 에이전트 공통 규칙(5줄)
2. `agents/<이름>/INSTRUCTIONS.md` — 자기 지시서 ([pickle](agents/pickle/INSTRUCTIONS.md) · [dot](agents/dot/INSTRUCTIONS.md))
3. `manifests/<주차>/<쇼핑몰>.md` — 이번 주 명세서 (현재 = [2026-W44/coupang.md](manifests/2026-W44/coupang.md))
4. 끝나면 [results/TEMPLATE.md](results/TEMPLATE.md) 형식으로 보고

## 사람(수빈)이 쓰는 것
- `prompts/pickle.md`, `prompts/dot.md` — 앱에 붙여 넣을 지시 프롬프트
- `results/` — 에이전트 보고를 파일로 보관(`EXP-01-pickle-2026-10-27.md` 식)

## 폴더
```
AGENTS.md                      공통 규칙
agents/pickle/INSTRUCTIONS.md  피클 지시서
agents/dot/INSTRUCTIONS.md     dot 지시서
manifests/2026-W44/coupang.md  명세서(쿠팡, 5품목)
results/TEMPLATE.md            보고 양식
prompts/                       사람이 복붙하는 프롬프트
```

원문(raw) 주소 규칙: `https://raw.githubusercontent.com/tsetse012/jangbogi-handoff/main/<경로>` — 저장소 연결이 안 되는 에이전트는 이 주소로 읽는다.
