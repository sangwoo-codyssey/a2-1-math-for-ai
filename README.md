# A2-1 - AI 학습을 수학으로 풀어보기 (math-for-ai)

> 🚧 **미착수** — 디렉터리·레포 준비만 완료

행렬 변환·Power Iteration·SVD(선형대수), 중심차분 수치 미분·Gradient(미적분),
2층 신경망 역전파 손계산, Vanilla GD·Momentum(최적화), MSE·Cross-Entropy 와 MLE 의 연결(확률)을
NumPy 로 직접 구현하고 시각화한다. 원문에 따르면 A6-1(AutoGrad 엔진)의 수학적 기반이 되는 미션이다.

- 과제 원문: 로컬 `../a2-1-math-for-ai.md`
- AI 심화 학습 · AI 수학 · 60시간 · 필수 · 개인
- Python 3.8 이상 (권장 NumPy >= 1.21, Matplotlib >= 3.4) · `np.random.seed(42)` 고정 · 그림은 `outputs/` 에 PNG

## 설치 및 실행

```bash
uv venv --python 3.12 .venv && source .venv/bin/activate
uv pip install -r requirements.txt   # uv 가 없으면 python -m venv .venv 후 pip install -r requirements.txt
```

진입점은 착수 때 정한다.

## 라이브러리 제약 (과제 §7)

| 구분 | 라이브러리 |
|---|---|
| 구현 | NumPy (모든 계산) |
| 시각화 전용 | Matplotlib, Seaborn |
| 검증 전용 | `np.linalg.eig` — Power Iteration 결과 비교에만, 고유값 계산 자체엔 금지 |
| 금지 | PyTorch·TensorFlow·JAX 등 자동 미분, scikit-learn 의 PCA·최적화 함수 |

코드 품질: 모든 클래스·함수에 Docstring, 수식은 주석 또는 Markdown, `requirements.txt` 에 버전 명시.

## 제출물 체크리스트

- [ ] `src/linear_algebra.py` — 회전·스케일링·전단 시각화, det 와 면적비 오차 1% 이내, Power Iteration(eig 대비 5% 이내), SVD 압축 k=10·50·100 비교
- [ ] `src/calculus.py` — 중심차분 수치 미분(x²의 x=3 에서 오차 1e-4 이내), 등고선 + Gradient 화살표
- [ ] `notebooks/backprop_derivation.ipynb` — 순전파·역전파 유도, 고정 예제 손계산(중간값 + shape 표기), NumPy 와 소수점 4자리 일치
- [ ] `src/optimizer.py` — VanillaGD·Momentum(β=0.9) 클래스, lr=0.1 수렴(원점 반경 0.1) / lr≥0.5 발산, x²+10y² 비교
- [ ] `notebooks/probability_loss.ipynb` — N(0,1)·N(2,0.5) PDF, B(0.3)·B(0.7) PMF, 소프트맥스 합 오차 1e-6, MSE=정규 MLE·CE=베르누이/카테고리 MLE 유도
- [ ] README — 개요·실행 방법·주요 결과 요약
- [ ] `requirements.txt`

## 보너스

- [ ] Adam 옵티마이저 (GD·Momentum·Adam 수렴 속도 비교)
- [ ] Newton Method (Hessian) vs 경사하강법
- [ ] 정보 이론 — 엔트로피·KL-Divergence·Cross-Entropy 직접 구현
