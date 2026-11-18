# Week 4

이번 주차에는 사전학습 모델을 네이버 쇼핑 리뷰로 **직접 파인튜닝**하고, 만든 모델을 **FastAPI로 감싸 API로 서빙**해봅니다.

> **📌  이번 실습은 가급적이면 Google Colab에서 진행해주세요!**

> 노트북을 실행하기 전에 런타임 유형을 **T4 GPU**로 바꿔주세요.

### 이번 주차의 학습 목표

- Fine-Tuning 파이프라인 구성
- 모델 서빙(Model Serving)의 개념과 필요성 이해
- FastAPI를 활용하여 모델을 API로 감싸는 구조 익히기

### Mission

[실습 노트북](week4_mission.ipynb)의 안내에 따라 각 단계의 코드를 살펴보고, 파인튜닝 학습을 실행하는 한 줄을 작성합니다.

개념 정리와 생각해보기는 노트북의 답변 셀에 작성해주세요.

- **Mission1 (파인튜닝 모델 구성하기)**: 네이버 쇼핑 리뷰 데이터의 전처리부터 학습 설정, 모델 학습과 평가, 예측까지 하나의 파인튜닝 파이프라인을 구성해봅니다.
- **Mission2 (FastAPI로 모델 서빙하기)**: 파인튜닝한 모델을 FastAPI로 서빙하고, 직접 요청을 보내 예측 결과를 확인해봅니다.

결과 해석은 실제 출력에 근거해 작성해주세요.
(이번 주차는 이전 주차의 결과 파일이 필요하지 않습니다.)

### 실행 전 확인

- 노트북의 첫 설치 셀을 실행해주세요. Colab과 로컬 모두 같은 셀을 사용합니다.
- 설치 후 커널(Colab은 세션)을 재시작하고, 다음 라이브러리 셀부터 실행해주세요.
- 실습 결과는 기본적으로 `artifacts/week4/`에 저장됩니다. 계속 사용할 모델은 Drive 등에 보관해주세요.

### 실습 관련 보충자료

| 자료 | 참고할 내용 | 읽을 부분 |
|---|---|---|
| [Hugging Face: Trainer API를 이용한 모델 미세 조정](https://huggingface.co/learn/llm-course/ko/chapter3/3) | `TrainingArguments`와 `Trainer`로 파인튜닝하는 방법 | 전체 |
| [FastAPI 공식 자습서](https://fastapi.tiangolo.com/ko/tutorial/) | FastAPI로 API 서버를 만드는 기본 방법 | 첫 걸음 & 요청 본문 |

전체 흐름은 [코스 개요](../README.md), 로컬 또는 Colab 설정은 [별도 실행 안내](../docs/runtime.md)를 확인해주세요.
