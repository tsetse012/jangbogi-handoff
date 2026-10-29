# 피클에 붙여 넣는 프롬프트 — 가격 조사(담지 않음)

`{목록}` 자리에 조사 목록 파일 경로를 바꿔 끼운다. 목록이 둘이면 **한 번에 하나씩, 두 번 실행**한다
(json 블록이 정확히 1개여야 해서 두 목록을 한 보고에 섞을 수 없다).

## 첫 조사
~~~
깃허브 저장소 tsetse012/jangbogi-handoff 를 열어서 AGENTS.md 와 agents/pickle/PRICECHECK.md 를 읽어. 저장소가 안 열리면 https://raw.githubusercontent.com/tsetse012/jangbogi-handoff/main/agents/pickle/PRICECHECK.md 로 읽어.
그 지시서대로 {목록} 표를 조사해서 상품명·판매가·판매 단위·배송 종류를 채팅 보고 끝에 json 코드블록 하나로 정리해줘. 장바구니에 담지 말고 결제도 하지 마. 와우 멤버십이 없어도 가격만 보면 되니 그대로 진행해.
~~~

예 (상위 50키 — 두 번 실행):
- 1회차: `{목록}` = `manifests/pricecheck/2026-10-30-top50-a.md` (1~25위)
- 2회차: `{목록}` = `manifests/pricecheck/2026-10-30-top50-b.md` (26~50위)

~~~
깃허브 저장소 tsetse012/jangbogi-handoff 를 열어서 AGENTS.md 와 agents/pickle/PRICECHECK.md 를 읽어.
그 지시서대로 manifests/pricecheck/2026-10-30-top50-a.md 표를 조사해서 json 코드블록 하나로 보고해줘. 담기·결제 금지.
~~~

## 재조사(이번 주 가격 갱신)
~~~
jangbogi-handoff 저장소의 agents/pickle/PRICECHECK.md 대로 {목록} 표를 조사해서 json 코드블록 하나로 보고해줘. 담기·결제 금지.
~~~

## 매주 예약(가격 이력 쌓기)
~~~
매주 일요일 저녁 7시에 jangbogi-handoff 저장소 agents/pickle/PRICECHECK.md 대로 {목록} 표를 조사하고, 채팅 보고 끝에 json 코드블록 하나로 결과를 정리해줘. 담기·결제는 하지 마.
~~~

## 엔진에 넣기(수빈이 직접)
```
# 첫 조사 1회만 --seed-caps 1.3 — price_cap(단가 상한)이 null 인 키에만
# 이번 보고의 최저 단가 × 1.3 으로 상한을 만든다(기존 상한은 덮어쓰지 않는다).
python3 engine/ingest.py --report <피클 보고.txt> --list <같은 목록 파일> --seed-caps 1.3 [--write]

# 두 번째 조사부터는 상한이 이미 있으므로 플래그 없이.
python3 engine/ingest.py --report <피클 보고.txt> --list <같은 목록 파일> [--write]
```
`--list` 가 목록의 `ingredient_key` 열을 요청 키로 쓴다 — 목록에 없는 키가 보고에 오면 병합하지 않는다.
