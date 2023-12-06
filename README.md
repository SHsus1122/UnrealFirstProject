# Destroy Object

### 파괴 가능한 사물들을 모두 파괴하면 승리하는 간단한 FPS 게임입니다.
> 에티버스 VR 16기 첫 프로젝트로 진행하게 되었으며, 위에서 말한 간단한 룰을 가진 게임입니다.

### 👉 [기획서 노션 주소](https://crocus-ermine-3b9.notion.site/79e799766f9740fa959243b754c197d8?pvs=4)

## 간단한 게임 Rule 소개
- 게임 내에서 스폰되는 파괴 가능한 사물들의 배치는 일부 랜덤으로 배치됩니다.
- 움직임이 있는 사물 또한 그 움직임의 속도나 이동반경이 랜덤으로 배치됩니다.
- 총 **3개의 Section 이 존재**하며 앞의 선행되는 Section 을 클리어해야 다음 Section 으로 가는 문을 통과하실 수 있습니다.
- 총은 **30 / 90** 발이 제공되며 총알은 필드 곳곳에 배치되며 한 탄창 다 사용시 재장전이 필요합니다.
- 점프 높이와 시간 관련한 아이템들이 필드 곳곳에 존재합니다.
- 총기는 `T` 키를 눌러 **단발, 2점사, 3점사, 연발** 총 4가지의 모드로 변경해서 사용 가능합니다.

## 프로젝트 기간
**2023.11.16 ~ 2023.12.06**

## 플레이 영상 👇

[![IU(아이유) _ Into the I-LAND](https://img.youtube.com/vi/iaVhPlkQHUE/0.jpg)](https://www.youtube.com/watch?v=iaVhPlkQHUE)

## 프로젝트 진행 간 주요 과제

- [x] MVP 패턴에 빗대어 GameState, Interface, GameMode 의 각각의 역할을 확실히 분리
    - GameState(Model) : 데이터를 저장하고 관리함으로서 단일성과 신뢰성을 유지
    - GameMode(Presenter) : 사용자에게 보여줄 데이터를 GameState에서 가져오거나 입력받은 데이터를 GameState에 가공하여 저장함으로서 게임 내의 Buiseness Logic을 구현하고 게임 내의 Rule을 관리
    - Interface : GameState와 GameMode의 의존성을 줄이고 정해진 역할만을 수행하도록 구성
    
    > GameState와 GameMode의 역할을 확실히 구분함으로서 작업의 효율과 개발 속도를 증진하였으며 Interace를 사용함으로 GameState와 GameMode의 모듈화를 진행하여 재사용성과 코드 수정에 유리하도록 관리하였습니다.
    > 
- [x]  파괴 가능한 Actor 에 개별 데미지 적용을 위한 Collision 스폰 및 오버랩 체크
    - 탄이 떨어지는 좌표에 Sphere Collision 를 스폰시켜서 해당 지점에 오버랩 된 액터를 배열에 담습니다. 이후, 해당 배열 안에 데미지 계산을 진행할 Actor 가 가진 HP 변수에 필요한 데미지를 축적시켜서 일정 수치 도달 시 MasterField 를 스폰해 해당 액터를 파괴합니다.
    - 위의 경우에 해당하지 않는 경우에는 해당 좌표에 MasterField를 스폰하게 됩니다.

