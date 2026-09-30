# Party Tactics — BG3 동료 AI / Companion AI

턴제 전투에서 **동료와 소환수를 AI 가 몹니다.** 최적의 로봇을 만드는 것이 목적이 아니라,
같이 싸우는 동료처럼 보이게 하는 것이 목적입니다 — 혼자 하는 유사 코옵 체험.

Turn-based combat AI that plays your **companions and summons** in Baldur's Gate 3.
The goal is not an optimal robot: it is a party that feels like a co-op partner.

> ## ⚠️ 시험판 / Pre-release
>
> 아직 다듬는 중입니다. 전투가 어색하거나 동료가 엉뚱한 선택을 할 수 있습니다.
> **세이브를 따로 떠 두고 쓰세요.**
>
> Work in progress. Expect rough edges. **Back up your saves.**

---

## 필요한 것 / Requirements

| | |
|---|---|
| Baldur's Gate 3 | Patch 8 기준으로 만들었습니다 / Built against Patch 8 |
| [Script Extender (BG3SE)](https://github.com/Norbyte/bg3se) | **필수** — 이 모드는 전부 SE Lua 로 돌아갑니다 / **Required** |

MCM(Mod Configuration Menu)은 **필요 없습니다** — 설정은 모드 자체 창(F11)에 있습니다.
MCM is **not** needed: all settings live in the mod's own window (F11).

## 설치 / Install

**모드 매니저 (권장 / recommended)**

1. 릴리즈에서 `PartyTactics-<버전>.zip` 을 받습니다 (안에 `PartyTactics.pak` 하나).
2. BG3 Mod Manager 에 끌어다 놓거나 Vortex 로 설치하고 켭니다.
   Drag the zip into BG3 Mod Manager, or install it with Vortex, then enable the mod.

**`.pak`**

1. 릴리즈에서 `PartyTactics-<버전>.pak` 을 받습니다.
2. `%LOCALAPPDATA%\Larian Studios\Baldur's Gate 3\Mods\` 에 넣습니다.
3. 모드 매니저(BG3 Mod Manager · Vortex)에서 켭니다.

**느슨한 파일 / Loose files** (매니저를 안 쓰거나 pak 이 안 먹을 때)

1. `PartyTactics-<버전>-loose.zip` 을 받습니다.
2. 안의 `Data` 폴더를 게임 설치 폴더에 덮어씁니다
   (`...\steamapps\common\Baldurs Gate 3\Data`).

지우려면 넣은 파일만 지우면 됩니다. 세이브에 남는 것은 없습니다.
To uninstall, just delete what you added. Nothing is written into your saves.

## 쓰는 법 / Usage

세이브를 불러오면 **Party Tactics 창**이 열립니다 (창 제목 옆에 여닫는 키가 보입니다).
**파티** 탭에서 캐릭터마다 **AI / 직접** 을 고르면, 전투에서 AI 로 맡긴 캐릭터의 차례를 AI 가 이어받습니다.
소환수는 주인을 따라갑니다.

When a save loads, the **Party Tactics window** opens (its title shows the key that opens/closes it).
In the **Party** tab, set each character to **AI** or **Direct**; in combat the AI plays the turns of the
characters you handed over. Summons follow their owner.

| 단축키 / Hotkey | 하는 일 / What it does |
|---|---|
| **F11** | 창 열기/닫기 · Open/close the window |
| **Ctrl + T** | 선택한 캐릭터를 직접 조종으로 (AI 가 행동 중이면 그 행동이 끝나고) · Take direct control of the selected character |
| **Ctrl + Y** | 선택한 캐릭터 AI 켜기/끄기 · Turn AI on/off for the selected character |

단축키는 **설정** 탭에서 바꿀 수 있습니다 (Ctrl · Shift · Alt 조합 가능).
Hotkeys can be changed in the **Settings** tab (Ctrl · Shift · Alt combos work).

### 차례 표시 / Turn display

AI 동료의 차례에는 그 동료 **머리 위**에 작은 표시가 뜹니다 — 먼저 "생각 중", 행동이 정해지면
**무엇을 · 누구에게** (주문 아이콘과 함께). 카메라가 그 동료를 따라갑니다 (설정에서 끌 수 있습니다).
**당신 차례**가 오면 당신 캐릭터 머리 위에 "당신 차례", 화면 위쪽에 "이름 · 당신 차례" 가 잠깐 뜨고 카메라가 당신 캐릭터로 돌아옵니다.
AI 동료와 차례를 함께 쓰면 **AI 가 먼저** 움직이고, 그동안의 클릭은 무시합니다 (Esc 나 Ctrl + T 로 풉니다).
화면 위쪽 한 줄 표시(마우스를 올리면 **고른 이유**)는 설정에서 켤 수 있습니다 (기본 꺼짐).

During an AI companion's turn a small label appears **above that companion**: first "Thinking", then
**what · on whom** with the spell icon. The camera follows it (can be turned off in Settings).
When **your turn** comes, "Your turn" appears above your character and briefly at the top of the screen, and the camera comes back to your character.
When AI companions share your turn, **they act first** and clicks are ignored until they finish (press Esc or Ctrl + T to click anyway).
The line at the top of the screen (hover it to see **why** it chose that) can be turned on in Settings (off by default).

## 설정 / Settings (F11 → Settings)

| 설정 / Setting | 고르는 것 / Options |
|---|---|
| 언어 · Language | 자동(게임 언어) · English · 한국어 — 한국어는 게임 언어가 한국어일 때만 (SE 창 글꼴) |
| 단축키 · Hotkey | 위 세 가지 / the three above |
| 차례 표시 · Turn display | 머리 위 표시(기본 켬) · 위쪽 줄(기본 끔) · 마우스를 올리면 이유 · 애니메이션 끄기 · AI 동료가 행동하는 동안 클릭 무시 · 카메라 따라가기(기본 켬) / label above the character (on) · line at the top (off) · reasons on hover · no animation · ignore clicks while an AI companion is acting · camera follows the AI companion (on) |
| 반응 · Reactions | 주문 슬롯을 쓰는 반응(방패 · 역주문 …)도 AI 가 쓸지 / let the AI use reactions that cost spell slots (Shield, Counterspell…) |
| 광역 주문 · Area spells | **아군 피격 허용 / 허용 안 함** — 허용이면 "적에게 주는 피해 − 아군 피해 × 4" 가 다른 행동보다 클 때만 씁니다 (Larian 의 적 AI 와 같은 무게) |
| 생각 시간 · Thinking time | **깊게**(기본 · 제한 없음) · **보통**(한 번에 약 4초) · **빠르게**(약 2초) — 시간이 다 되면 그때까지 찾은 최선 |
| 주문 슬롯 · Spell slots | 자동(보스급 적이 있으면 아끼지 않기) · 항상 아끼기 · 항상 아끼지 않기 |

광역 주문은 설정과 관계없이 **직접 조종하는 캐릭터**, **쓰러진 아군**, **맞으면 쓰러질 수 있는 아군**이 범위에 있으면 쓰지 않습니다.
Regardless of the setting, area spells are never cast onto a character you control directly, a downed ally,
or an ally the spell could knock down.

## 무엇을 보고 고르나 / What it reasons about

게임 데이터를 직접 읽습니다 — 주문 · 상태 · 부스트 · 조건 함수 · 물건.
이름으로 특별 취급하는 목록이 아니라, 그 행동이 실제로 만드는 **결과의 값**으로 고릅니다.

- 쓰러진 동료 일으키기, 치유, 집중 끊기, 자원 아끼기
- 자리 — 사선 · 고저차 · 위험 표면 · 기회공격 · 실제 걸어갈 길 (다른 몸 · 계단식 턱 · 사다리)
- 두루마리 (생환 두루마리로 죽은 동료 되살리기 등) · 치유 물약 던지기 — 물건은 게임 AI 의 물건 할인 그대로 아껴 씁니다
- 사거리 · 기회공격 반경 · 치명타 · 낙하 피해 · 밀치기와 던지기 거리 · 명중 유리/불리는 게임이 계산하는 식 그대로
- 원거리 공격은 주문의 투사체 궤적 자료로 곡선을 그려 벽 · 지형 · 동료에 막히는지 보고, 막히면 쏘지 않고 트인 자리로 옮겨 쏩니다
- 높은 곳에서 쏠 수 있으면 그 자리에서 쏩니다 (게임이 다른 자리로 걸려 보내지 않게)
- 짧은 자리 옮기기(6m 미만)에는 점프 · 순간이동을 쓰지 않고, 횟수가 정해진 순간이동(안개 걸음 등)은 적 곁에서 빠지거나 옮긴 자리에서 곧바로 행동이 닿을 때만 씁니다
- 기회공격을 부르거나 공중에서 끊길 점프는 고르지 않고, 순간이동 착지는 게임이 받아 주는 자리로 고릅니다
- 소환수도 같이 몹니다

## 버그 제보 / Bug reports

**설정 → 그 밖 → 제보용 기록 만들기** 를 누르면 파일 하나가 생깁니다:
`%LOCALAPPDATA%\Larian Studios\Baldur's Gate 3\Script Extender\PartyTactics\report_1.txt`
(칸 셋을 돌려 씁니다 — `report_1~3`). [Issues](../../issues) 에 이 파일과 함께 어떤 전투에서 무엇이 어떻게 보였는지 적어 주세요.
평소에 쓰는 파일은 설정 파일(`Script Extender\party_tactics_settings.json`) 하나뿐입니다.

Press **Settings → Other → Create debug report** to write one file (three rotating slots, `report_1~3`) under
`Script Extender\PartyTactics\`, and attach it to an [issue](../../issues). Otherwise the mod only writes its
settings file (`Script Extender\party_tactics_settings.json`).

## 알려진 한계 / Known limits

- 물약을 **마시는** 것은 아직 안 합니다 (던지기만).
- 멀리 던진 물건이 지형에 막히는지는 던지기 전에 아직 못 가립니다.
- 오래 남는 구름 · 장판에 동료가 나중에 걸어 들어가는 경우는 광역 주문 규칙이 아직 안 봅니다.
- 특수 기믹이 있는 전투는 아직 손대지 않았습니다.
- 적이 아주 많은 전투에서는 동료 한 명이 몇 초씩 생각할 수 있습니다 — 설정의 **생각 시간**으로 줄일 수 있습니다.
- 멀티플레이 · 패드는 시험하지 않았습니다 (카메라 따라가기는 혼자 하는 판 기준입니다). / Multiplayer and controllers are untested.

## 소스 / Source

개발 저장소는 비공개입니다. 이 저장소는 배포용입니다.
The development repository is private; this one exists for releases.
