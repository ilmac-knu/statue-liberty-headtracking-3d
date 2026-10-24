# 자유의 여신상 — 헤드 트래킹 3D 돌출 착시

일반 노트북 또는 스마트폰의 **전면 카메라**로 얼굴 위치를 추적하고, 얼굴 움직임에 따라 자유의 여신상을 바라보는 **원근 시점**이 달라지는 실험입니다.

**중요:** 실제 홀로그램이나 화면 밖 광학 투영이 아닙니다. 가상 창틀과 비대칭 원근 투영을 활용한 **헤드 트래킹 기반 3D 착시**이며, 엄밀한 의미의 MR 공간 배치와도 구별됩니다.

## 필요한 파일

```text
statue-liberty-headtracking-3d/
├── index.html
├── README.md
└── statue_of_liberty_1.glb
```

GLB는 기존 프로젝트에서 사용하던 동일한 파일을 저장소 최상위에 업로드하세요. ZIP 파일에는 용량을 줄이기 위해 GLB를 포함하지 않았습니다.

## 배포

1. GitHub에 `statue-liberty-headtracking-3d` 저장소를 생성합니다.
2. 위 세 파일을 최상위에 업로드합니다.
3. **Settings → Pages → Deploy from a branch → main / (root) → Save**.
4. 배포 후 다음 주소로 접속합니다.

https://ilmac-knu.github.io/statue-liberty-headtracking-3d/

## 체험

1. **노트북**에서 페이지를 열고 자유의 여신상이 표시되는지 확인합니다.
2. `📷 얼굴 추적 시작`을 눌러 카메라 접근을 허용합니다.
3. 노트북을 고정한 채 **머리를 좌우·상하로 움직여** 시점 변화를 확인합니다.
4. `■ 얼굴 추적 종료`를 누르면 카메라가 꺼집니다.
5. 얼굴 추적을 시작하지 않아도 마우스 드래그로 시점 변화 효과를 미리 확인할 수 있습니다.
6. **스마트폰**에서는 기기를 고정하고 전면 카메라를 켜 같은 방식으로 실험합니다.

## 구현 원리와 한계

- Three.js의 **비대칭 투영(off-axis projection)** 으로 가상의 화면 평면을 기준으로 카메라 시점을 계산합니다.
- MediaPipe Face Detection을 통해 얼굴 중심 위치를 추정합니다.
- 이 예제는 얼굴의 **2차원 위치 변화**를 이용하는 입문형 시점 추적입니다. 얼굴까지의 실제 거리나 두 눈의 3차원 위치를 정밀하게 측정하지는 않습니다.
- 따라서 실제 화면 밖에 3D 물체가 투영되지는 않으며, 입체 착시 강도는 화면 크기, 시청 거리, 조명 등에 따라 다릅니다.
- 카메라 영상은 브라우저에서 얼굴 추적에 사용되며, 이 예제는 영상을 서버로 업로드하는 코드를 포함하지 않습니다. 단, Three.js/MediaPipe 라이브러리는 인터넷 CDN에서 불러옵니다.
- HTTPS가 필요하며 브라우저에서 카메라 권한을 허용해야 합니다.

## 저작자 표시

자유의 여신상 3D 모델: **tech.service.allwe**, [Sketchfab 원본](https://sketchfab.com/3d-models/statue-of-liberty-1-b3105217169b4ebbabeefb1d97e3696c), [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).

## 기술

Three.js · MediaPipe Face Detection · WebGL · getUserMedia
