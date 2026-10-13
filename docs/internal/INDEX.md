# Gitea 전용 내부 문서 궤적 마스터 인덱스 (Internal Documentation Index)

본 문서는 프로젝트 개발 전 과정의 의사결정 맥락, 기술적 수식, 구현 궤적을 타임라인 순으로 영구 보존하는 마스터 인덱스입니다.

---

## 누적 작업 궤적 목록 (Timeline Index)

| 턴 번호 | 주요 작업 주제 및 핵심 요약 | 쉬운말 작업궤적 문서 | 엔지니어링 세부문서 |
| :---: | :--- | :--- | :--- |
| **Turn 001** | **만화 데포르메 인지 과학 분석, 안면 디테일 깎임 역설 해결 및 스트로크 굵기 보존**<br>- [같은 오브젝트 = 같은 선굵기] 연속성 유지 원칙 구현<br>- 안면 잡선 135개 미적 감산(Aesthetic Omission)을 통한 잉크 떡짐 해소<br>- 미적 순도 지수 $Q$ 최대 616.9% 폭증 실측 및 3D 에뮬레이터 검증 | [trajectory_manga_deformer_ko.md](file:///c:/Users/ms338/Documents/antigravity/etch-a-sketch-3d-lab/docs/internal/trajectory_manga_deformer_ko.md) | [engineering_manga_deformer_details.md](file:///c:/Users/ms338/Documents/antigravity/etch-a-sketch-3d-lab/docs/internal/engineering_manga_deformer_details.md) |
| **Turn 002** | **전체 연산 파이프라인 분석, 복잡도 프로파일링(병목점 규명) 및 비-AI 기하 시멘틱 분해 원리**<br>- 6단계 엔드투엔드 파이프라인 시간 복잡도 실측<br>- 99.8% 병목 원인 규명: 78.6만 노드 픽셀 그리드 상 488회 스텔스 A* 탐색<br>- 딥러닝 없이 기하/위상/인체계측학 3대 수학 법칙으로 달성한 시멘틱 분해 원리 정립 | [turn_002_work_log_easy.md](file:///c:/Users/ms338/Documents/antigravity/etch-a-sketch-3d-lab/docs/internal/turn_002_work_log_easy.md) | [turn_002_engineering_spec.md](file:///c:/Users/ms338/Documents/antigravity/etch-a-sketch-3d-lab/docs/internal/turn_002_engineering_spec.md) |
| **Turn 003** | **위치/스케일 특정성 완전 제거(Affine-Invariant), 딕셔너리 기반 고속도로 LUT 라우터 가속(470x)**<br>- $(0.5W, 0.33H)$ 고정 좌표 폐기: 2차 모멘트 기반 자율 피사체 중심 및 타원 추적<br>- 절대 픽셀($\text{px}$) 폐기: 특성 스케일 $L_{\text{char}}$ 및 무차원 분위수($p_{15}, p_{70}, p_{90}$) 적용<br>- TraceIt/LZ 압축 융합 고속도로 사전 LUT 구축: 134초 $\rightarrow$ 285ms (470배 가속)<br>- Auto-Linking Mesh로 도화지 가로지름 수직선 100% 박멸 및 3D 실기 렌더링 검증 | [turn_003_work_log_easy.md](file:///c:/Users/ms338/Documents/antigravity/etch-a-sketch-3d-lab/docs/internal/turn_003_work_log_easy.md) | [turn_003_engineering_spec.md](file:///c:/Users/ms338/Documents/antigravity/etch-a-sketch-3d-lab/docs/internal/turn_003_engineering_spec.md) |
| **Turn 004** | **가중치 연동 차이킨 곡선형 수렴(Curvilinear Convergence) 및 홈 역주행/잠수 레일 스텔스 라우터**<br>- 얇은 선일수록 타원형 곡선 수렴 원칙: 가중치 계층별 차이킨 코너 컷팅(안면/텍스처 2회 분할)<br>- 무도화지 노출 원칙: 이미 긁힌 홈 안을 역주행(Backtracking)하여 시각 노출 비용 $0.0$ 은닉 달성<br>- 홈 역주행 20회 + 잠수 고속도로 65회 재활용으로 도화지 위 잔선 100% 박멸<br>- 3D 실기 렌더링 캡처 및 시각적 만족 지표 실측 검증 완료 | [turn_004_work_log_easy.md](file:///c:/Users/ms338/Documents/antigravity/etch-a-sketch-3d-lab/docs/internal/turn_004_work_log_easy.md) | [turn_004_engineering_spec.md](file:///c:/Users/ms338/Documents/antigravity/etch-a-sketch-3d-lab/docs/internal/turn_004_engineering_spec.md) |

---
*Last Updated: 2026-10-13*
