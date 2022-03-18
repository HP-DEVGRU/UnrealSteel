# UNREAL STEEL

상태: 중단  
종류: 팀  
포지션: 개발, 기획, 아이디어, 팀장  

[https://github.com/HP-DEVGRU/UnrealSteel](https://github.com/HP-DEVGRU/UnrealSteel)

# Introduction

기존의 하드웨어 기반 모션 캡쳐 기술을 비전 AI으로 구현한 서비스입니다. 카메라로 사용자의 모션을 인식하고 이를 3D로 복원, 실시간 motion data를 애니메이션화하여 rigging 작업을 거쳐  게임엔진에 렌더링시킵니다. 사용자는 자신의 동작대로 가상의 캐릭터를 조종할 수 있습니다.  

# Motivation

**Unreal Steel : Unreal Engine + Real steel**  

**Unreal Engine(게임엔진)**  

![UNREAL%20STE%20b58db/unreal-for-motion-designer-2.gif](images/unreal-for-motion-designer-2.gif)

**Real Steel (영화)**  

![UNREAL%20STE%20b58db/MaxAtom.gif](images/MaxAtom.gif)

영화 속 장면을 게임엔진으로 구현해보고자 시작하게 되었습니다.  

# Main Technology

## Previous Motion Capture

기존의 모션캡쳐 기술은 센서가 달린 수트와 헬멧을 쓰고 센서의 좌표 데이터를 수신하면서 이루어졌습니다. **하지만 모션캡쳐 장비와 소프트웨어들이 너무 비싸서** 높은 진입장벽이 형성되었습니다. 또한 배우가 직접 움직인 데이터만 얻을 수 있다는 단점이 있었습니다.  

![UNREAL%20STE%20b58db/0cb2e38d5f7244125aedb72c2386b802.gif](images/0cb2e38d5f7244125aedb72c2386b802.gif)  

![UNREAL%20STE%20b58db/8f02eb1cff9d643eb370802eac703cbf.gif](images/8f02eb1cff9d643eb370802eac703cbf.gif)  

![UNREAL%20STE%20b58db/304f7bd122687db3c1db0f1d3c96d8ca.gif](images/304f7bd122687db3c1db0f1d3c96d8ca.gif)  

## Ours

저희 Unreal Steel은 사용자가 카메라 하나만 있으면 그 자리에서 즉시 모션캡쳐 기술을 사용할 수 있도록 해줍니다. 심지어 모션이 담긴 유튜브 영상으로도 움직임을 캡쳐할 수 있습니다. 이는 일반 사용자에게 face app같은 컨텐츠 제공용으로 쓰일 수도 있고 컨텐츠 크리에이터에게 더 다양한 컨텐츠를 제작할 수 있도록 도와주는 툴이 될 것입니다.  

![UNREAL%20STE%20b58db/ezgif-6-c7ce93a8df3c.gif](images/ezgif-6-c7ce93a8df3c.gif)  

![순서 : 위(좌→우)→아래(우→좌)](images/output_livelink.gif)  

순서 : 위(좌→우)→아래(우→좌)  

# **Goals**

## From

![UNREAL%20STE%20b58db/tenor_(1).gif](images/tenor_(1).gif)  

## To

![UNREAL%20STE%20b58db/tenor.gif](images/tenor.gif)  

**In Real-Time!!**

# Achievement

![UNREAL%20STE%20b58db/Untitled.png](images/Untitled.png)  

# Now

현재 프로젝트는 중지되었습니다. 좌표를 retargetting하는 과정에서 지속적인 오류가 발생합니다.  

1. **bone의 개수와 위치가 다릅니다**. 논문으로 구현해서 복원한 3D 좌표는 16개인데 반해 언리얼 엔진은 최소 18개를 요구합니다. 또한 bone retargetting을 구현하기 위해서는 T자 포즈를 취하고 동기화하는 과정이 필요한데 우리의 모델은 일반 포즈를 복원한 것이기 때문에 T자 포즈를 취할 수 없습니다.
2. **디버깅이 너무 힘듭니다.** Unreal Engine은 오류가 발생하면 오류가 발생했다고 report 한 뒤 종료됩니다. log를 남겨도 피상적인 내용만 report하고 내부에서 어떻게 동작되는지 알 수 없습니다.
3. **커뮤니티가 없습니다.** 저희와 같은 프로젝트를 진행한 사람은 한명도 없으며 언리얼 엔진 개발자 커뮤니티 또한 활발하지 않아 자료도 없고 레퍼런스도 없고 아무것도 없습니다. 심지어 언리얼 엔진은 거의 한달마다 새로운 버전을 출시하기 때문에 여러 프로그램에 종속성이 있는 환경에서 개발이 불가능에 가깝습니다. (있는 자료들마저 버전이 모두 다름)
4. **인원이 없습니다**. 프로젝트 인원이 총 3명이었는데 1명은 캐릭터 디자인(게임 엔진에서 나를 따라할 캐릭터), 1명은 예측 모델 모델링 (모션캡쳐, 3D 좌표 복원)을 담당하였고, 나머지 부분(추출된 3D 좌표를 애니메이션화, 리깅 작업, T-pose synchronize, 데이터 통신 등)을 제가 담당했습니다. 해당 도메인 지식이 전무한 상태에서 도메인 지식을 쌓느라 개발을 진행할 수 없게 되고 이는 개발기간의 연장으로 이어졌습니다.

![애니메이션화까진 구현한 모습](images/output.gif)  

애니메이션화까진 구현한 모습  

![언리얼 엔진 캐릭터와 동기화에 실패한 모습](images/ezgif-6-e7acb2e5592c.gif)  

언리얼 엔진 캐릭터와 동기화에 실패한 모습  

# Development Documents

[개발일지](https://www.notion.so/e4677b69256741b285abf4c7cf6070d0)
