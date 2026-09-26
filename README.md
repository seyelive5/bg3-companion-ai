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
| Baldur's Gate 3 | Patch 8 기준으로 만들었습니다 |
| [Script Extender (BG3SE)](https://github.com/Norbyte/bg3se) | **필수** — 이 모드는 전부 SE Lua 로 돌아갑니다 |

## 설치 / Install

**`.pak` (권장)**

1. 릴리즈에서 `PartyTactics-<버전>.pak` 을 받습니다.
2. `%LOCALAPPDATA%\Larian Studios\Baldur's Gate 3\Mods\` 에 넣습니다.
3. 모드 매니저(BG3 Mod Manager · Vortex)에서 켭니다.

**느슨한 파일 (매니저를 안 쓰거나 pak 이 안 먹을 때)**

1. `PartyTactics-<버전>-loose.zip` 을 받습니다.
2. 안의 `Data` 폴더를 게임 설치 폴더에 덮어씁니다
   (`...\steamapps\common\Baldurs Gate 3\Data`).

지우려면 넣은 파일만 지우면 됩니다. 세이브에 남는 것은 없습니다.
To uninstall, just delete what you added. Nothing is written into your saves.

## 쓰는 법 / Usage

전투가 시작되면 동료 차례를 AI 가 이어받습니다. 게임 안에서 **F11** 로 패널을 엽니다 —
누가 AI 에 맡겨졌는지, 무엇을 왜 골랐는지, 설정이 거기 있습니다.

Combat starts and the AI takes over companion turns. Press **F11** in game for the panel:
who is on AI, what it picked and why, and the settings.

## 무엇을 보고 고르나 / What it reasons about

게임 데이터를 직접 읽습니다 — 주문 · 상태 · 부스트 · 조건 함수 · 물건.
이름으로 특별 취급하는 목록이 아니라, 그 행동이 실제로 만드는 **결과의 값**으로 고릅니다.

- 쓰러진 동료 일으키기, 치유, 집중 끊기, 자원 아끼기
- 자리 — 사선 · 고저차 · 위험 표면 · 기회공격 · 실제 걸어갈 길 (다른 몸 · 계단식 턱 · 사다리)
- 두루마리 (생환 두루마리로 죽은 동료 되살리기 등) · 치유 물약 던지기 — 물건은 게임 AI 의 물건 할인 그대로 아껴 씁니다
- 사거리 · 기회공격 반경 · 치명타 · 낙하 피해 · 밀치기와 던지기 거리 · 명중 유리/불리는 게임이 계산하는 식 그대로
- 소환수도 같이 몹니다

## 알려진 한계 / Known limits

- 물약을 **마시는** 것은 아직 안 합니다 (던지기만).
- 멀리 던진 물건이 지형에 막히는지는 던지기 전에 아직 못 가립니다.
- 특수 기믹이 있는 전투는 아직 손대지 않았습니다.
- 적이 아주 많은 전투(적 20명 안팎)에서는 동료 한 명이 생각하는 데 몇 초씩 걸릴 수 있습니다.

## 소스 / Source

개발 저장소는 비공개입니다. 이 저장소는 배포용입니다.
The development repository is private; this one exists for releases.

버그 제보는 [Issues](../../issues) 로 — 어떤 전투에서 무엇이 어떻게 보였는지 적어 주시면 됩니다.
