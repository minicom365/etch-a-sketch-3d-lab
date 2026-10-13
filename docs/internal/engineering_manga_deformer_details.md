# [엔지니어링 세부문서] 만화 데포르메(Déformer) 인지 과학 수식화, 안면 미적 감산(Aesthetic Omission) 및 위계적 스트로크 굵기 보존

> **연계 쉬운말 작업궤적**: [trajectory_manga_deformer_ko.md](file:///c:/Users/ms338/Documents/antigravity/etch-a-sketch-3d-lab/docs/internal/trajectory_manga_deformer_ko.md)

---

## 1. 아키텍처 개요 및 인지 과학 모델링

### 1.1 학술적 이론 배경
- **Scott McCloud (1993) *Understanding Comics***: *Amplification through Simplification*. 감정 이입을 위한 안면 상징 기호화 및 여백의 미(Negative Space).
- **Cole et al. (ACM SIGGRAPH 2008) *Where Do People Draw Lines?***: 외곽 실루엣은 고가중치(Heavy Line Weight), 안면 내부는 초미세선(Hairline Weight) 및 선택적 생략(Selective Omission).
- **게슈탈트 비시각적 완결성 (Amodal Completion)**: 불필요한 음영 선을 제거하고 공백을 둘 때 뇌의 시각 피질이 부드러운 피부 면으로 자동 인지.

### 1.2 안면 디테일 깎임 역설 (Detail Clipping Paradox)
- $1024 \times 768$ 해상도 캔버스에서 안면 영역 크기는 대략 $160 \times 130\text{px}$, 안구는 $15\sim 20\text{px}$.
- 고정 굵기($1.9\text{px}$)와 분말 번짐 헤일로($4.2\text{px}$)가 쌍꺼풀/속눈썹/동공 윤곽선 사이(간격 $< 2\text{px}$)를 채우며 잉크 떡짐(Ink Clogging) 발생.
- 기존 방식의 좌표 기반 원형 절단은 머리카락/의복 스트로크 중간에서 굵기 불연속성(Pop) 초래.

---

## 2. 수식화 및 알고리즘 구현

### 2.1 스트로크 객체 단위 4대 추상화 계층 분류기
스트로크 $S = \{ (x_k, y_k) \}_{k=1}^N$에 대해 중심 좌표 $(\bar{x}, \bar{y})$, 누적 길이 $L_S$, 바운딩 박스 면적 $A_{\text{bbox}}$를 산출:

$$\left(\frac{\bar{x} - x_{\text{face}}}{R_x}\right)^2 + \left(\frac{\bar{y} - y_{\text{face}}}{R_y}\right)^2 \le 1.0 \implies S \in \text{Zone}_{\text{face}}$$

계층 부여 규칙:
1. **Silhouette**: $(S \in \text{Loop} \land A_{\text{bbox}} > 0.08 W H) \lor L_S > 350\text{px} \implies w = 1.00$ ($1.9\sim 2.0\text{px}$)
2. **Clothing & Hair Major**: $L_S \ge 70\text{px} \lor (S \in \text{Loop} \land L_S \ge 45\text{px}) \implies w = 0.74$ ($1.4\text{px}$)
3. **Internal Texture**: 기타 내부 선분 $\implies w = 0.58$ ($1.1\text{px}$)
4. **Facial Anchor**: 안면 핵심 구조 $\implies w = 0.48$ ($0.9\text{px}$)

단일 스트로크 내의 모든 점 $(x_k, y_k)$에 대해 동일한 $w_S$를 부여하여 **[같은 오브젝트 = 같은 선굵기]**를 보장.

### 2.2 안면 미적 감산 필터 (Aesthetic Omission)
안면 영역($S \in \text{Zone}_{\text{face}}$) 내에서:
- 필수 앵커 보존 조건:
  - 안구 폐곡선: $S \in \text{Loop} \land 18 \le L_S \le 180$
  - 상안검 / 입술: $S \in \text{Open} \land L_S \ge 24$
  - 콧망울 점: $L_S \le 16 \land |\bar{x} - x_{\text{face}}| \le 0.35 R_x \land |\bar{y} - (y_{\text{face}} + 20)| \le 0.35 R_y$
- 잡선 생략(Pruning) 조건:
  - 앵커가 아니면서 $L_S < 22\text{px}$ 이거나, 뺨 구역($\bar{y} > y_{\text{face}} - 15 \land |\bar{x} - x_{\text{face}}| > 0.25 R_x$)에 위치하는 잔선.

### 2.3 미세선 지터 댐핑 (Negative Space Damping)
1D 평활 노이즈 기반 아날로그 진동 인가 시, 섬세한 여백 보존을 위해 가중치 연동 진폭 적용:

$$\text{Amplitude}(w) = \begin{cases} 
0.08 & \text{if } w < 0.6 \text{ (Facial Anchor)} \\
0.15 & \text{if } 0.6 \le w < 0.8 \text{ (Clothing/Texture)} \\
0.22 & \text{if } w \ge 0.8 \text{ (Silhouette/Stealth Rail)}
\end{cases}$$

---

## 3. 정량 검증 결과

실제 선화 이미지 3종에 대한 실측 지표 ($Q = \text{Negative Space Ratio} / \text{Clogging Ratio}$):

| 대상 이미지 | 기법 | 잉크 떡짐률 | 여백률 | 미적 순도 $Q$ | HVS MAE | 오차 분산 ($\sigma^2$) |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **`Gx7Pj7MbUAAWlmn`** | 1차 기하 원형 | 33.18% | 47.37% | 1.43 | 0.0982 | 0.045405 |
| | **2차 미적 감산 + 계층 보존** | **10.18%** | **59.66%** | **5.86 (+311.3%)** | **0.0680** | **0.025917** |
| **`GxbV8vUbsAAE99T`** | 1차 기하 원형 | 43.26% | 35.39% | 0.82 | 0.1514 | 0.061474 |
| | **2차 미적 감산 + 계층 보존** | **9.41%** | **55.43%** | **5.89 (+616.9%)** | **0.1004** | **0.035137** |
| **`GxNWn5OaIAQnF_7`** | 1차 기하 원형 | 32.29% | 49.85% | 1.54 | 0.2061 | 0.063073 |
| | **2차 미적 감산 + 계층 보존** | **17.58%** | **57.01%** | **3.24 (+109.9%)** | **0.1316** | **0.037006** |

---

## 4. 형상 관리 및 파일 변경점
- `presets/sketch_fox.json`: 1024x768 해상도 4대 계층 가중치($w$) 및 안면 잡선 135개 생략 적용 완료.
- `etch-a-sketch-3d-lab/light-screentone.js`: 스트로크 단위 계층 분류 및 안면 감산 필터 알고리즘 이식.
- `light-screentone/light-screentone.js`: 동일 알고리즘 동기화 완료.
- `index.html`: `scratchSegment` 듀얼 패스(Halo + Core) 동적 스케일링 렌더러 연동.
