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

지우려면 넣은 파일만 지우면 됩니다 (느슨한 파일은 `Data\Mods\PartyTactics` · `Data\Public\PartyTactics` 두 폴더). 세이브에 남는 것은 없습니다.
To uninstall, just delete what you added (for loose files, the `Data\Mods\PartyTactics` and `Data\Public\PartyTactics` folders). Nothing is written into your saves.

## 쓰는 법 / Usage

세이브를 불러오면 **Party Tactics 창**이 열립니다 (창 제목 옆에 여닫는 키가 보입니다).
**파티** 탭에서 캐릭터마다 **AI / 직접** 을 고르면, 전투에서 AI 로 맡긴 캐릭터의 차례를 AI 가 이어받습니다.
소환수는 주인을 따라갑니다.

When a save loads, the **Party Tactics window** opens (its title shows the key that opens/closes it).
In the **Party** tab, set each character to **AI** or **Direct**; in combat the AI plays the turns of the
characters you handed over. Summons follow their owner.

파티 탭에서 동료의 역할을 **소환사**로 고르면 아래에 **소환사** 구획이 생깁니다. 쓸 소환 주문을 체크해 두면 첫 차례에 체크한 소환을 먼저 쓰고,
그 뒤로는 아직 나와 있지 않은 것을 차례마다 하나씩 부릅니다 (구획의 두 칸으로 끌 수 있습니다).

If you set a companion's role to **Summoner** in the Party tab, a **Summoners** section appears below. Check the summon spells it should use:
it casts a checked summon on its first turn, then calls one checked summon that is not out yet each turn (two checkboxes there turn this off).

| 단축키 / Hotkey | 하는 일 / What it does |
|---|---|
| **F11** | 창 열기/닫기 · Open/close the window |
| **Ctrl + T** | 선택한 캐릭터를 직접 조종으로 (AI 가 행동 중이면 그 행동이 끝나고) · Take direct control of the selected character |
| **Ctrl + Y** | 선택한 캐릭터 AI 켜기/끄기 · Turn AI on/off for the selected character |
| **Ctrl + F** | 마우스로 가리킨 적에 집중 지시 (적이 아닌 곳을 가리키고 누르면 풀림) · Focus the enemy under the cursor (press it pointing anywhere else to clear) |

단축키는 **설정** 탭에서 바꿀 수 있습니다 (Ctrl · Shift · Alt 조합 가능 — 0.8.1 까지는 조합 단축키가 먹지 않았습니다. 0.8.2 에서 고쳤습니다).
Hotkeys can be changed in the **Settings** tab (Ctrl · Shift · Alt combos work — they did nothing up to 0.8.1; fixed in 0.8.2).

### 팀 집중 / Team focus

AI 동료들은 팀이 가장 빨리 쓰러뜨릴 수 있는 적 하나를 같이 노리고, 다친 적을 마무리합니다. 무엇을 할지는 예전처럼 정하고 **공격할 적만** 팀 기준으로 고릅니다.
적을 가리키고 **Ctrl + F** 를 누르면 그 적에 집중하라고 지시합니다 — 닿는 AI 동료는 그 적을 치거나 묶고, 못 닿으면 그쪽으로 다가갑니다
(쓰러진 동료 일으키기 · 자기 목숨이 위급할 때는 예외). 집중 표적은 그 적 머리 위에 문장으로 보입니다 — 금색 **지시 · 집중** (체력 막대와 함께) 은 내가 지시한 적, 흐린 **AI · 팀 집중** 은 AI 동료들이 함께 노리는 적.
설정의 **표적 고르기** 를 끄면 동료마다 각자 고릅니다.

AI companions gang up on the one enemy the team can take down fastest and finish off the wounded. They decide what to do as before; **only the enemy they attack** changes.
Point at an enemy and press **Ctrl + F** to order a focus: AI companions who can reach it attack or hold it, the rest move toward it
(except to help up a downed ally or to save themselves). The focus target is marked above its head: gold **Order · Focus** (with a health bar) for the enemy you ordered, dim **AI · Team focus** for the enemy the AI companions are ganging up on.
Turn off **Target choice** in Settings to let each companion pick its own target.

### 차례 표시 / Turn display

AI 동료의 차례에는 그 동료 **머리 위**에 금빛 메달과 리본이 뜹니다 — 먼저 "생각 중" (도는 문양), 행동이 정해지면 주문 아이콘과
**무엇을 · 누가 ▸ 누구에게**, 둘째 줄에 **명중 · 쓰러뜨릴 확률** (치유면 회복량). 카메라가 그 동료를 따라갑니다 (설정에서 끌 수 있습니다).
**당신 차례**가 오면 당신 캐릭터 머리 위에 "당신 차례", 화면 위쪽에 "이름 · 당신 차례" 가 잠깐 뜨고 카메라가 당신 캐릭터로 돌아옵니다.
AI 동료와 차례를 함께 쓰면 **AI 가 먼저** 움직이고, 그동안의 클릭은 무시합니다 (Esc 나 Ctrl + T 로 풉니다).
화면 위쪽 한 줄 표시(마우스를 올리면 **고른 이유**)는 설정에서 켤 수 있습니다 (기본 꺼짐).

During an AI companion's turn a gold medal and ribbon appear **above that companion**: first "Thinking" (a turning rune), then the spell icon with
**what · who ▸ on whom**, and a second line with the **chance to hit or take the target down** (or the amount healed). The camera follows it (can be turned off in Settings).
When **your turn** comes, "Your turn" appears above your character and briefly at the top of the screen, and the camera comes back to your character.
When AI companions share your turn, **they act first** and clicks are ignored until they finish (press Esc or Ctrl + T to click anyway).
The line at the top of the screen (hover it to see **why** it chose that) can be turned on in Settings (off by default).

## 설정 / Settings (F11 → Settings)

| 설정 / Setting | 고르는 것 / Options |
|---|---|
| 언어 · Language | 자동(게임 언어) · English · 한국어 — 한국어는 게임 언어가 한국어일 때만 (SE 창 글꼴) |
| 단축키 · Hotkey | 위 네 가지 / the four above |
| 차례 표시 · Turn display | 머리 위 표시(기본 켬) · 위쪽 줄(기본 끔) · 마우스를 올리면 이유 · 애니메이션 끄기 · AI 동료가 행동하는 동안 클릭 무시 · 카메라 따라가기(기본 켬) · 집중 표적 머리 위 표시(기본 켬) / label above the character (on) · line at the top (off) · reasons on hover · no animation · ignore clicks while an AI companion is acting · camera follows the AI companion (on) · mark the focus target above its head (on) |
| 반응 · Reactions | 주문 슬롯을 쓰는 반응(방패 · 역주문 …)도 AI 가 쓸지 / let the AI use reactions that cost spell slots (Shield, Counterspell…) |
| 광역 주문 · Area spells | **아군 피격 허용 / 허용 안 함** — 허용이면 "적에게 주는 피해 − 아군 피해 × 4" 가 다른 행동보다 클 때만 씁니다 (Larian 의 적 AI 와 같은 무게) |
| 소환 주문 · Summons | 전투 중에 AI 가 소환 주문 쓰기 (기본 켬) — 끄면 이미 불러낸 소환수만 움직입니다 / let the AI cast summon spells in combat (on by default); when off, summons already out still act |
| 표적 고르기 · Target choice | **팀 집중**(기본 켬 — 한 적을 같이 쓰러뜨린다) · 끄면 동료마다 각자 / **team focus** (on by default — gang up on one enemy) · off: each companion picks its own target |
| 생각 시간 · Thinking time | **깊게**(기본 · 제한 없음) · **보통**(한 번에 약 4초) · **빠르게**(약 2초) — 시간이 다 되면 그때까지 찾은 최선 |
| 주문 슬롯 · Spell slots | 자동(보스급 적이 있으면 아끼지 않기) · 항상 아끼기 · 항상 아끼지 않기 |
| 물건 쓰기 · Items | 두루마리 · 폭탄 · 물약 · 특수 화살마다 **안 씀 · 아끼기**(게임의 적 AI 와 같은 기준) **· 보통**(기본) **· 아끼지 않기** — 파티 탭의 **캐릭터별 물건 쓰기**에서 캐릭터마다 따로 / for scrolls · bombs and grenades · potions · special arrows: Don't use · Save · Normal (default) · Never save — also per character in the Party tab (**Items by character**) |

동료는 **자기 가방의 물건만** 씁니다 (가방 속 주머니까지). 쓰게 하려면 그 동료에게 건네 주세요.
아끼기는 자기 주문 · 공격보다 3배쯤 좋을 때만, 보통은 1.7배쯤, 아끼지 않기는 같거나 좋으면 씁니다 — 쓰면 없어지니 작은 이득에는 (특히 마지막 하나는) 아낍니다.
네 종류에 안 드는 물건 (도구 · 이야기 물건 · 음식 등) 은 쓰지 않습니다.

Companions use **only the items in their own inventory** (including pouches inside it) — give an item to the companion who should use it.
Save uses an item only when it is about 3 times better than the companion's own spells and attacks, Normal about 1.7 times, Never save when it is at least as good.
Items outside these four kinds (tools, story items, food…) are not used.

광역 주문은 설정과 관계없이 **직접 조종하는 캐릭터**, **쓰러진 아군**, **맞으면 쓰러질 수 있는 아군**이 범위에 있으면 쓰지 않습니다.
Regardless of the setting, area spells are never cast onto a character you control directly, a downed ally,
or an ally the spell could knock down.

## 무엇을 보고 고르나 / What it reasons about

게임 데이터를 직접 읽습니다 — 주문 · 상태 · 부스트 · 조건 함수 · 물건.
이름으로 특별 취급하는 목록이 아니라, 그 행동이 실제로 만드는 **결과의 값**으로 고릅니다.

- 쓰러진 동료 일으키기, 치유, 집중 끊기, 자원 아끼기
- 자리 — 사선 · 고저차 · 위험 표면 · 기회공격 (몬스터의 발톱 · 물기 같은 타고난 공격까지) · 실제 걸어갈 길 (다른 몸 · 계단식 턱 · 사다리)
- 다음 적 차례 — 적마다 누구를 칠지 (근접은 가까운 쪽 · 원거리는 닿는 사람에게 고르게 · 맞히기 쉬운 쪽을 조금 더) 와 동료마다 쓰러질 확률 (이미 붙은 불타기 같은 지속 피해까지) 을 셉니다. 설 자리 · 소환 자리 · 치유 물약을 마실지에 씁니다
- 팀 집중 — 위 "팀 집중" 처럼 공격할 적을 팀 기준으로 (집중 표적 · 다친 적 마무리)
- 가방의 물건 — 두루마리 (생환 두루마리로 죽은 동료 되살리기 등) · 폭탄 (동료가 휘말리지 않게 적에게 — 종류마다 얼마나 빗나가는지 던져 보며 배우고, 던진 동료 · 곁의 동료가 맞을 몫도 셉니다) ·
  물약 (동료에게 던져 치유하고, 싸움에 도움이 될 때 보조 행동으로 스스로 마십니다 — 치유 물약은 HP 가 절반 밑이거나 곧 크게 다칠 것 같을 때만, 비약 · 독 · 기름은 안 씁니다) · 특수 화살
- 던질 물건은 게임이 실제로 날릴 곡선이 지형 · 장식물에 걸려 표적 앞에 떨어질 자리에서는 던지지 않고, 치유 물약은 가는 길의 몸 · 튐 범위의 적 (적도 치유된다) 까지 봅니다
- 무기를 떨어뜨리면 (금속 가열 등) 위험하지 않을 때 걸어가 자기 무기를 주워 다시 들고, 무기가 없는 동안에는 무기 기술을 쓰지 않습니다
- 주문을 쓴 뒤에는 그 동작이 끝날 때까지 기다렸다가 걷거나 다음 주문을 씁니다 (물약을 마신 뒤에도)
- 이미 묶인 적에게 같은 턴을 막는 제어 주문을 낭비하지 않고, 잠들었거나 최면 무늬에 걸린 적은 다른 적이 남아 있는 동안 건드리지 않습니다 (마지막 적이거나 한 번에 쓰러뜨릴 수 있으면 칩니다)
- 수호자 역할은 가장 위협적인 적을 먼저 도발하고, 분명히 더 나은 행동이 없으면 그 적을 노립니다
- 쌍둥이 주문처럼 표적을 늘리는 토글은 서로 다른 표적을 고릅니다 (둘째 표적이 없으면 토글 없이 씁니다)
- 시전자 둘레에 피해를 주는 외침 주문 (비하의 팔 · 파괴의 물결 · 새벽의 광휘) 은 시전자 자신을 표적으로 냅니다 (게임이 그렇게 받습니다)
- 행동 급증처럼 행동을 늘려 주는 기술은 덤 행동으로 할 일까지 짜서 씁니다 (적이 하나뿐이면 같은 적을 한 번 더)
- 돌진 공격 같은 돌진 · 소환한 포박 덩굴의 끌어당기기 · 시체 소생 · 언데드 창조 (이 전투에서 죽은 몸 — 아직 덜 시험했습니다)
- 한 차례에 여러 행동을 짤 때 직업 자원 · 명중할 때 드는 비용 (손 얹기 횟수 · 강타 등) 을 같이 세고, 빗나가 안 치렀으면 남은 것으로 다시 짭니다
- 사거리 · 기회공격 반경 · 치명타 · 낙하 피해 · 밀치기와 던지기 거리 · 명중 유리/불리는 게임이 계산하는 식 그대로
- 시전하기 전에 게임이 보는 것을 같이 봅니다 — 켜 둔 토글의 비용 (못 내면 그 시전 동안 끄고 쓴 뒤 다시 켭니다) · 실명 중 시야 거리 · 화살 기술이 요구하는 원거리 무기 · 게임의 주문 시야 (계획할 때와 쏘기 직전이 같은 기준) · 갑옷을 입은 아군에게는 마법 갑옷을 쓰지 않습니다
- 게임이 거부한 행동은 같은 전투에서 처지 (자원 · 상태 · 무기) 가 그대로면 다시 시도하지 않습니다
- 원거리 공격은 게임이 실제로 날릴 궤적으로 벽 · 지형 · 적 몸에 막히는지 보고 (같은 편 몸은 투사체가 지나갑니다), 막히면 쏘지 않고 트인 자리로 옮겨 쏩니다. 쏠 때는 트인 궤적을 게임이 고르게 합니다
- 높은 곳에서 쏠 수 있으면 그 자리에서 쏩니다 (게임이 다른 자리로 걸려 보내지 않게)
- 다가가서 쏘는 대부분의 주문은 걷기와 시전을 한 동작으로 하고, 걸은 뒤에는 실제로 선 자리에서 남은 행동을 다시 짭니다. 자리를 옮길 때 드는 이동력은 실제로 걸을 길로 잽니다
- 게임이 걸어갈 길을 못 찾으면 그 걸음을 멈추고 다시 짭니다 (예전에는 게임이 목적지로 옮겨 놓아 순간이동처럼 보였습니다)
- 걸어서 못 닿는 행동은 점프 · 이동 주문 한 번을 섞은 길 (지금 자리에서 뛰기 · 걷다가 뛰기) 로 닿는지 보고 값으로 견줍니다
- 자리를 고치려고 6m 미만을 옮길 때는 점프 · 순간이동을 쓰지 않고 (옮긴 자리에서 곧바로 행동이 닿을 때 · 위험 표면에서 빠질 때는 예외), 횟수가 정해진 순간이동(안개 걸음 등)은 적 곁에서 빠지거나 옮긴 자리에서 곧바로 행동이 닿을 때만 씁니다
- 기회공격을 부르거나 공중에서 끊길 점프는 고르지 않고, 점프 · 순간이동 착지는 게임이 받아 주는 자리로 고릅니다 (곁의 몸 · 발밑 높낮이)
- 불 · 용암 같은 위험 표면은 차례 끝 · 다음 차례 시작에 받을 피해까지 셉니다. 머물면 쓰러질 것 같으면 빠지는 것이 먼저입니다
- 적이 밀쳐 용암 · 낭떠러지로 떨어뜨릴 수 있는 자리 (밀치기 · 밀어내는 주문 · 폭발 화살) 는 그 위험을 값으로 셉니다 — 차례를 마칠 자리 · 다가가 멈출 자리 · 시전할 자리 모두
- 소환 주문 — 적 곁 · 지킬 동료 앞 · 자기 곁 가운데 소환수가 가장 쓸모 있는 자리에 부릅니다. 자리는 게임이 받아 주는 곳으로 고르고 (다른 몸 · 문 · 큰 소환수가 턱에 걸치는 바닥을 피합니다) 한 차례에 둘을 부르면 자리를 나눕니다. 싸울 힘이 없는 패밀리어 · 애완동물은 쓰지 않습니다
- 시전자 앞 직사각형 범위 주문 (천둥파 · 번개 줄기 · 돌풍) 은 게임과 같은 규칙으로 맞을 몸을 셉니다 — 벽 · 문 뒤의 몸은 빼고, 표적에 닿지 않는 자리에서는 쓰지 않습니다
- 적에게 조종당한 동료 (정신 지배 등) 는 AI 가 몰지 않고 게임에 맡깁니다 (사람이 조종할 때와 같습니다)
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

- 먼 동료에게 던진 치유 물약이 던진 동료의 손에서 깨져 자기를 치유하는 일이 있습니다 (한 전투에서 두 번 — 원인을 조사하고 있습니다). / A healing potion thrown at an ally far away can break in the thrower's hands and heal the thrower instead (seen twice in one fight; being looked into).
- 물에 선 적에게 번개 주문을 쓰면 물웅덩이 전체가 감전되어 같은 물에 선 동료도 다칠 수 있습니다 — 광역 주문 규칙은 주문 범위 안의 아군만 봅니다. / A lightning spell aimed at an enemy standing in water can electrify the whole pool and hurt allies standing in it.
- 밀치기 같은 주문이 가끔 동료가 올라갈 수 없는 자리 (예: 위쪽 턱) 를 고릅니다 — 잠깐 멈칫한 뒤 다른 행동을 합니다. / Shove and similar spells sometimes pick a spot the companion cannot walk up to (such as a ledge above it); it pauses briefly and does something else.
- 다가가서 쏘는 주문의 걸음이 가끔 실패합니다 — 동료가 다른 행동을 합니다. / When a spell needs a few steps first, the walk sometimes fails and the companion does something else.
- 오래 남는 구름 · 장판에 동료가 나중에 걸어 들어가는 경우는 광역 주문 규칙이 아직 안 봅니다.
- 특수 기믹이 있는 전투는 아직 손대지 않았습니다.
- 적이 아주 많은 전투에서는 동료 한 명이 몇 초씩 생각할 수 있습니다 — 설정의 **생각 시간**으로 줄일 수 있습니다.
- 멀티플레이 · 패드는 시험하지 않았습니다 (카메라 따라가기는 혼자 하는 판 기준입니다). / Multiplayer and controllers are untested.

## 소스 / Source

개발 저장소는 비공개입니다. 이 저장소는 배포용입니다.
The development repository is private; this one exists for releases.
