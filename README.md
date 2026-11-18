# Palace Project (Legacy)

《클레르 옵스퀴르: 33 원정대》에서 영감을 받아 만든 3D 턴제 RPG입니다.
던전을 탐험하다 적과 마주치면 턴제 전투로 넘어가고, 적의 공격 타이밍에 맞춰 패링과 회피를 할 수 있습니다.

취업을 준비하며 공부용으로 만든 프로젝트이며, 2025년 당시의 코드를 그대로 보존한 저장소입니다.

- 플레이 영상: https://youtu.be/riH7HTbKuA8
- 엔진: Unity 6 (6000.0.33f1), URP

## 이 저장소에 들어 있는 것

**직접 작성한 코드만** 들어 있습니다. 에셋 스토어에서 받은 모델·애니메이션·이펙트·UI 팩은 라이선스상 재배포할 수 없어 포함하지 않았습니다.
그래서 이 저장소만 받아서는 프로젝트를 열어 실행할 수 없습니다. 실제 동작은 위 플레이 영상에서 볼 수 있습니다.

| 경로 | 내용 |
|---|---|
| `Assets/05_Scripts/` | 게임 코드 전체 |
| `Assets/Utility/`, `Assets/00098_Utility/` | 입력 처리와 공용 컴포넌트 |
| `Packages/manifest.json` | 사용한 Unity 패키지 목록 |
| `ProjectSettings/ProjectVersion.txt` | 엔진 버전 |

## 구현한 것

### 1. 탐험 (Encounter)

- 캐릭터 조작, 적의 정찰·추적
- 상호작용 오브젝트, 인벤토리와 장비 슬롯
- 적과 접촉하면 전투로 전환

### 2. 전투 (Battle)

- 페이즈 방식의 턴 진행과 행동 순서 대기열
- QTE 입력
- 패링·회피 판정

### 3. 스킬과 적 AI

- 애니메이션 이벤트에 맞춘 대미지 적용
- 공통 인터페이스(`ISkill`)로 스킬 등록
- 행동 트리 기반 적 AI

### 4. 연출

- 타임라인 이벤트와 카메라 전환
- 사운드

## 코드 구조

```
Assets/05_Scripts/
├── BattleField/      전투 진행(BattleSystem), 턴 페이즈(Phase), 전투 UI(BattleUI)
├── SkillScripts/     스킬 정의와 플레이어·적 스킬 동작
├── Player/           플레이어 이동·전투·애니메이션·스킬·상태
├── Enemy/            적 이동·전투·행동 트리·감지 영역
├── Character/        플레이어와 적이 함께 쓰는 기반 클래스
├── Inventory/, Item/ 인벤토리, 장비 슬롯, 아이템 정의
├── Interactable/     문, 스위치, 체크포인트 등 상호작용 오브젝트
├── Cinematic/        카메라와 타임라인 재생
├── Events/           튜토리얼과 보스전 이벤트
├── Effect/, Audio/   이펙트와 사운드
└── UI/, UI_Pause/    화면 UI와 일시정지 메뉴
```

## 사용한 외부 에셋 (미포함)

Synty(Polygon 시리즈), ARPG 애니메이션 팩, KriptoFX, Polygon Arsenal, INab Studio Toon Pro, Stylized Dragon Pack 등
에셋 스토어의 모델·애니메이션·이펙트·UI 팩을 사용했습니다.

## 참고

이 프로젝트는 구조를 다시 잡는 리뉴얼을 따로 진행할 예정입니다. 이 저장소는 리뉴얼 이전의 원본 코드입니다.
