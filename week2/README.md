# Week 2

이번 주차에는 Week1에서 준비한 데이터를 **실제로 모델에 학습시키는 단계**로 넘어갑니다. “AI가 데이터를 학습하며 패턴을 익히는 과정”을 직접 경험해봅시다!

### 이번 주차의 학습 목표

- 감정 분석 모델의 구조 이해
- 모델 학습과 손실, 정확도 확인
- 검증 데이터와 테스트 데이터의 역할 이해
- Epoch 수에 따른 학습 곡선과 과적합 비교

### Mission

[실습 노트북](week2_mission.ipynb)의 안내에 따라 필요한 이론을 살펴보고 핵심 코드를 작성합니다.

개념 정리와 생각해보기는 노트북의 답변 셀에 작성해주세요.
마지막에는 10 Epoch과 30 Epoch의 학습 결과를 비교하며, 과적합이 나타나는지 확인해보아요.
설정 선택과 결과 해석은 실제 출력에 근거해 작성해주세요.

입력 파일은 Week1에서 저장한 `artifacts/week1/week1_state.json`입니다.
Colab에서는 JSON을 업로드하거나 Drive를 연결한 뒤, 노트북의 `STATE_PATH`를 파일 위치에 맞게 바꿔주세요.


### 실습 관련 보충자료

| 자료 | 참고할 내용 | 읽을 부분 |
|---|---|---|
| [딥 러닝을 이용한 자연어 처리 입문: 7장 딥 러닝 개요](https://wikidocs.net/22882) | 개념 정리 중 이해가 어려운 내용이 있을 때 참고하세요 | 7장에서 필요한 부분을 골라 읽기. [07-04 딥 러닝의 학습 방법](https://wikidocs.net/36033) 중 손실함수, 옵티마이저 |
| [TensorFlow: 단어 임베딩](https://www.tensorflow.org/text/guide/word_embeddings?hl=ko) | 단어를 학습 가능한 벡터로 바꾸는 과정 | 단어 임베딩 & Embedding 레이어 사용 예시 |
| [TensorFlow: 과대적합과 과소적합](https://www.tensorflow.org/tutorials/keras/overfit_and_underfit?hl=ko) | 학습을 오래 할 때 과적합이 생기는 이유와 검증 손실의 변화 | 도입부의 과적합 설명 & '과대적합 예제'의 모델별 손실 곡선 |

### 모델 학습 관련 선택 읽기

| 자료 | 참고할 내용 | 읽을 부분 |
|---|---|---|
| [TensorFlow: 모델 저장과 복원 (한국어)](https://www.tensorflow.org/tutorials/keras/save_and_load?hl=ko) | 학습 도중 모델을 저장하고 다시 불러오는 방법 | 훈련하는 동안 체크포인트 저장하기 & 체크포인트 콜백 사용하기|

전체 흐름은 [코스 개요](../README.md), 로컬 또는 Colab 설정은 [별도 실행 안내](../docs/runtime.md)를 확인해주세요.
