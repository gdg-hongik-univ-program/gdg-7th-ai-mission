# Week 1

이번 주차에는 상품 리뷰를 숫자로 바꾸는 **데이터 전처리**를 진행합니다.

### 이번 주차의 학습 목표

- 텍스트 데이터의 구조 이해
- 학습, 검증, 테스트 데이터 분리
- 전처리 파이프라인 구축
- 문장 길이 시각화

### Mission

[실습 노트북](week1_mission.ipynb)의 안내에 따라 필요한 이론을 살펴보고 핵심 코드를 작성합니다.
제공된 검토 코드를 실행해 결과를 확인하고, 그 의미를 해석해봅시다.

마지막에는 길이 그래프를 해석하고 노트북과 전처리 상태를 저장합니다.  
설정 선택과 결과 해석은 실제 출력에 근거해 작성해주세요.
전처리 결과의 기본 저장 위치는 프로젝트 루트의 `artifacts/week1` 폴더입니다.

### 실습 관련 보충자료

| 자료 | 참고할 내용 | 읽을 부분 |
|---|---|---|
| [Google MLCC: 데이터 세트 분할](https://developers.google.com/machine-learning/crash-course/overfitting/dividing-datasets?hl=ko) | 학습, 검증, 테스트의 역할과 데이터 중복으로 생기는 누수 | "학습, 검증, 테스트 세트"와 "테스트 세트의 추가 문제" |
| [D2L: 텍스트를 시퀀스로 바꾸기](https://d2l.ai/chapter_recurrent-neural-networks/text-sequence.html) | 텍스트 정제, 토큰화, 어휘 사전과 미등록 토큰 처리 | 9.2.1~9.2.3 |
| [TensorFlow: 전처리 레이어](https://www.tensorflow.org/guide/keras/preprocessing_layers?hl=ko) | 어휘 사전의 저장과 추론에서 같은 전처리를 사용하는 이유 | "adapt() 메서드"와 "추론 시 모델 내에서 전처리를 수행할 때의 이점" |
| [TensorFlow: 영화 리뷰 텍스트 분류](https://www.tensorflow.org/tutorials/keras/text_classification?hl=ko) | 정수 인코딩, 패딩, 잘림과 학습 데이터로만 어휘를 만드는 이유 | "훈련을 위한 데이터세트 준비하기" |

### 모델 학습 관련 선택 읽기

| 자료 | 참고할 내용 | 읽을 부분 |
|---|---|---|
| [TensorFlow: 훈련 루프 처음부터 작성하기](https://www.tensorflow.org/guide/keras/writing_a_training_loop_from_scratch?hl=ko) | 순전파, 손실 계산, 기울기 계산과 가중치 갱신 | "GradientTape 사용하기: 첫 번째 엔드 투 엔드 예시" |
| [D2L: 순전파와 역전파](https://d2l.ai/chapter_multilayer-perceptrons/backprop.html) | 계산 그래프와 연쇄법칙으로 이해하는 역전파 | 5.3.1~5.3.4 |

전체 흐름은 [코스 개요](../README.md), 로컬 또는 Colab 설정은 [별도 실행 안내](../docs/runtime.md)를 확인해주세요.
