# UE × AI FieldGuide — AI 3D Asset Pipeline

> ## ⚠️ 언리얼 프로젝트를 연 뒤 반드시 Fab 의 Unfinished Building 애셋을 추가하세요
> 언리얼 프로젝트를 열고 나서 **Fab 의 [Unfinished Building](https://www.fab.com/listings/25f2e7e5-5cca-48a5-99a3-35c38b8240ac) 애셋을 프로젝트에 추가해야 합니다.**
> 이 애셋은 이 저장소에 들어 있지 않습니다. Fab 에서 받아 추가합니다.
>
> **After opening the Unreal project, you must add the [Unfinished Building](https://www.fab.com/listings/25f2e7e5-5cca-48a5-99a3-35c38b8240ac) asset from Fab to the project.**
> This asset is not included in this repository. Get it from Fab.

영상 「[UE x AI] FieldGuide」 실습에서 쓴 파일입니다.

| 폴더 | 내용 |
|---|---|
| `01_concept` | 컨셉 지침(`Rules`)과 컨셉 이미지 |
| `02_sheets` | 3D 생성에 넣은 시트 이미지 — `probe`(탐사선 본체 · 카메라 시점별), `props`(주변 소품) |
| `03_tirpo` | Tripo 에서 생성한 로우폴리곤 |
| `07_FBX_for_UE_import` | 언리얼로 가져갈 FBX |
| `UE_Proj_v58` | 언리얼 엔진 5.8 프로젝트 (`ai3dAssetsPipeline.uproject`) |

하이폴리곤 파일은 용량 때문에 별도 링크로 공유합니다.

`UE_Proj_v58` 에는 Tripo Bridge 플러그인이 들어 있지 않습니다. Tripo Studio 에서 언리얼로 바로 보내려면 [Tripo](https://www.tripo3d.ai) 에서 Tripo Bridge(UE 5.8) 플러그인을 받아 `UE_Proj_v58/Plugins/` 에 넣습니다. 프로젝트를 열고 들어 있는 애셋을 보는 데에는 이 플러그인이 필요하지 않습니다.
