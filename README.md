# 🎮 Project Sanzo (내일배움캠프 언리얼 7기 6조 CH3 프로젝트)

## 📖 프로젝트 소개

Project Sanzo는 내일배움캠프 언리얼 7기 6조의 챕터 3(CH3) 과정을 위해 개발된 언리얼 엔진 C++ 기반 [게임 장르 입력, 예: 3D 액션 RPG] 게임입니다.

객체 지향 프로그래밍(OOP) 설계와 언리얼 프레임워크를 적극적으로 활용하여 구현되었으며, 깃허브(GitHub) PR 템플릿과 브랜치 전략을 통해 체계적인 팀 협업을 진행했습니다.

- 개발 기간: 202X.XX.XX ~ 202X.XX.XX (약 X주)
- 개발 엔진: Unreal Engine 5.x
- 사용 언어: C++ (99.1%), Blueprints
- 협업 툴: GitHub, Slack, Notion

## 👨‍💻 팀원 소개 및 역할

| 이름 | 역할 | 담당 업무 (세부 구현 내용) | GitHub |
| :-: | :-: | :-: | :-: |
| [이름] | 플레이어 캐릭터 & 전투 시스템 | - 캐릭터 상태 및 스탯 제어: GameplayTag 기반의 유연한 상태(조준, 회피, 패링 등) 관리 및 SanzoStatComponent를 통한 스태미나(소모/회복/탈진) 로직 구현<br>- 전투 시스템 구현: 무적 시간(I-Frame)이 포함된 회피 및 방향별 피격 리액션 구현<br>- 고도화된 패링 시스템: 패링 성공/실패 몽타주 분기, 스팸 방지 패널티, 성공 시 슬로우 효과 및 데미지 반사 로직 적용<br>- 성장 및 상호작용: 인터페이스(Interface)를 활용한 모듈화된 레벨업/경험치 시스템 설계 및 외형 변신 업그레이드 연동<br>- 애니메이션 및 카메라: Aim Offset 적용, 조준 시 카메라 줌, 무기 스왑 및 장착 소켓(Socket) 동기화 | [@kbrother102](https://github.com/kbrother102) |
| [이름] | 적 AI & 몬스터 설계 | - 다양한 적 객체 구현: 근접(Melee), 원거리(Ranged) 및 보스(Boss) 몬스터 베이스 클래스 설계 및 블루프린트 연동<br>- 행동 트리(BT) 기반 AI: Behavior Tree와 Blackboard를 활용한 상태(순찰, 추적, 공격) 기반 인공지능 패턴 구현<br>- 보스전 특수 로직: 체력 비례 2페이즈(Phase) 전환, 공격 범위 가변화 및 페이즈 전용 사운드/이펙트 연동<br>- 전투 상태 피드백: 적 피격 및 스턴(Stun) 상태 애니메이션 몽타주 구현 및 무기/아이템 콜리전 겹침 버그 최적화 | [@djkim12](https://github.com/djkim12) |
| [이름] | UI & 시스템 프로그래밍 | - UI 시스템 (UMG): 메인 메뉴, 인게임 HUD, 팝업 UI 구현 및 예외 처리(버튼 중복 클릭 방지 등)<br>- 업그레이드 시스템: DataTable 기반의 플레이어 강화 시스템(공격력 한도, 유도탄 확률 등) 데이터 설계 및 적용<br>- 게임 플로우 제어: GameState, PlayerController를 활용한 전반적인 게임 상태 관리 및 트루 엔딩 미디어(Media) 재생 연출 구현<br>- 편의성(UX) 컴포넌트: 플레이어의 길 안내를 돕는 네비게이션 화살표(NavigationArrow) 구현 | [@JRoLee](https://github.com/JRoLee) |
| [이름] | 게임 코어 루프 & 레벨 디자인 | - 게임 코어 및 스테이지 제어: GameMode, GameState, StageManager, RoomBase를 연동한 웨이브/전투 흐름 및 스테이지 클리어 로직 구현<br>- 레벨 디자인 및 환경 최적화: 맵의 특성에 맞춘 Nav Mesh 볼륨 최적화 및 동적 환경 제어<br>- 환경 상호작용 객체: 파괴 가능한 오브젝트(도자기 등) 콜리전 처리 및 기믹 구현<br>- 사운드 제어: 글로벌 BGM On/Off 토글 기능 및 스테이지/전투 페이즈별 사운드 환경 구축 | [@yoonseo](https://github.com/yoonseo) |
| [이름] | 무기 시스템 & 특수 기믹 | - 무기 및 총기 베이스 구현: SanzoWeaponBase와 파생된 SanzoGun 클래스를 통해 핵심 무기 발사 및 데미지 처리 로직 구현<br>- 업그레이드 투사체 연동: 유도 미사일(Missile) 업그레이드 발동 조건 및 동적 데미지 산정 로직 적용<br>- 원거리 적 특수 패턴: 원거리 몬스터(Ranged)의 나이아가라(Niagara) 기반 레이저 조준선(Aim Laser) 연동 및 타겟팅 기믹 구현 | [@GitHubID](https://github.com/ID) |

## 🌟 주요 기능 (Key Features)

### 1. 플레이어 전투 및 컨트롤 (Player Mechanics)
- GameplayTag를 활용한 정교한 캐릭터 상태 제어.
- 스태미나 기반의 액션 시스템(탈진, 회복)과 무적 프레임(I-Frame)이 적용된 회피 로직.
- 리스크 & 리턴이 확실한 패링 시스템 (스팸 방지, 데미지 반사, 타임 슬로우 효과).
- 인터페이스 기반의 모듈화된 레벨업 및 외형/스탯 업그레이드 연동.

### 2. 적 AI 및 다크소울식 보스전 (Enemy AI & Boss Fight)
- AI Controller, Behavior Tree(BT), Blackboard를 활용한 상태 기반 적 AI 구현.
- 근접/원거리 적의 다양한 공격 패턴 및 스턴(Stun) 상태 이상 구현.
- 나이아가라(Niagara) 이펙트를 활용한 원거리 적의 레이저 조준선(Aim Laser) 및 타겟팅 시스템.
- 보스 몬스터 특수 패턴: 체력 비례에 따른 페이즈 전환(2페이즈) 및 공격 범위 변화 등 긴장감 있는 보스전 구현.

### 3. 유기적인 스테이지 흐름 및 게임 루프 (Stage & Core Loop)
- SanzoStageManager와 SanzoRoomBase를 활용한 모듈화된 스테이지 및 몹 웨이브 관리.
- 파괴 가능한 오브젝트(도자기 등)를 통한 환경 상호작용 및 파밍 요소.
- 최적화된 Nav Mesh를 통해 AI의 매끄러운 추적 경로 보장.

### 4. 무기 및 업그레이드 시스템 (Weapon & Upgrade)
- C++ 상속을 활용한 무기 베이스(SanzoWeaponBase) 및 총기(SanzoGun) 클래스 설계.
- 콜리전 트레이스를 통한 정교한 타격 판정 및 유도 미사일(Missile) 발사 기믹 구현.
- DataTable을 연동한 무기별 공격력, 공격 속도 제어 및 확률 기반 플레이어 강화(Upgrade) 시스템 지원.

### 5. UI 및 UX 편의성 (UI & Experience)
- 팝업 및 중복 클릭 방지가 적용된 안정적인 UUserWidget 기반 인터페이스.
- NavigationArrow 컴포넌트를 활용한 직관적인 목표 길찾기 안내.
- 유저 편의성을 고려한 인게임 BGM 토글 시스템 및 엔딩 시네마틱 재생 연출.

## 📁 프로젝트 구조 (Directory Structure)

```text
7th-Team6-CH3-Project/  
├── Config/ # 프로젝트 설정 파일 (Input, Engine, Game 등)  
├── Content/ # 에셋 폴더 (블루프린트, 맵, 메쉬, 머티리얼, UI 등)  
├── Source/  
│ └── ProjectSanzo/ # 메인 C++ 소스 코드  
│   ├── Character/ # 플레이어 캐릭터 로직 (GameplayTags, Component 등)  
│   ├── AI/ # 일반 몬스터 및 보스 AI 클래스  
│   ├── Weapon/ # 무기 베이스 및 Gun 클래스 등   
│   ├── Stage/ # RoomBase, StageManager 등 스테이지 제어 로직  
│   ├── GameMode/ # 게임 모드, 게임 스테이트, 데이터 테이블 로직  
│   ├── Controller/ # 플레이어 컨트롤러 및 AI 컨트롤러  
│   └── UI/ # UMG 위젯 C++ 기반 메인 UI, HUD 클래스  
├── .gitattributes  
├── .gitignore  
├── pull_request_template.md # 팀 협업을 위한 PR 템플릿  
└── ProjectSanzo.uproject # 언리얼 엔진 프로젝트 실행 파일
```

## 📸 스크린샷 및 플레이 영상 (Screenshots & Gameplay)

| 메인 화면 | 보스전 및 무기 장착 화면 |
| :---: | :---: |
| | |

*(이곳에 프로젝트 시연 영상 링크나 GIF를 추가하세요)*

---

## 💻 설치 및 실행 방법 (How to Build and Run)

> **⚠️ 주의:** 본 프로젝트의 캐릭터 모델링을 정상적으로 로드하기 위해서는 **VRM4U 플러그인**이 필수적으로 요구됩니다.

1. 이 저장소를 로컬 컴퓨터로 클론합니다.  
   ```bash
   git clone [https://github.com/NbcampUnreal/7th-Team6-CH3-Project.git](https://github.com/NbcampUnreal/7th-Team6-CH3-Project.git)
   ```
   플러그인 설치: VRM4U GitHub Releases 페이지에서 사용 중인 언리얼 엔진 5 버전에 맞는 플러그인을 다운로드한 후, 프로젝트 최상단 경로에 Plugins 폴더를 생성하고 압축을 해제하여 넣습니다.

2. 프로젝트 폴더로 이동하여 ProjectSanzo.uproject 파일을 우클릭합니다.

3. Generate Visual Studio project files를 클릭하여 .sln 파일을 생성합니다.

4. 생성된 ProjectSanzo.sln 파일을 Visual Studio 2022로 엽니다.

5. 솔루션 구성이 Development Editor / Win64로 되어 있는지 확인하고 빌드(Ctrl + Shift + B) 합니다.

6. 빌드가 완료되면 .uproject 파일을 더블 클릭하여 언리얼 에디터를 실행합니다.

7. 에디터 툴바에서 Play(플레이) 버튼을 눌러 게임을 실행합니다.
