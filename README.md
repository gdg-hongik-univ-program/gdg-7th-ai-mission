# AI 미션코스

기본 AI 이론과 Python을 바탕으로 데이터 준비부터 모델 학습·평가·활용까지 경험해봅시다. Keras와 실제 프로젝트가 처음인 수강생을 대상으로 합니다.

### 4주 동안 무엇을 할까요?

| 주차 | 할 일 | 이론과 도구 | 남길 결과 |
|---|---|---|---|
| [1주차](week1/README.md) | 리뷰 데이터 준비 | 분리·정제·벡터화 → scikit-learn, Python re, Keras TextVectorization | 세 집합·어휘·설정·길이 그래프 |
| 2주차 | 감정 분류 모델 학습·평가 | Embedding·일반화·과적합 → Keras Embedding/Pooling/Dense, fit/evaluate | 모델·학습 곡선·실패 사례 |
| 3주차 | BERT 이해, 배송·환불 RAG | 사전학습·검색 후 생성 → Transformers, FAISS, Qwen | 검색 근거·답변 비교 |
| 4주차 | 파인튜닝·서빙 | 모델 조정·저장·요청/응답 → Transformers, FastAPI | 저장 모델·tokenizer·호출 결과 |

1→2주차는 같은 전처리를 사용합니다. BERT는 해당 모델의 tokenizer를 사용하고, RAG는 별도의 문서 기반 실습입니다.

학습은 가중치·bias를 조정하고, 추론은 정해진 파라미터로 새 입력의 출력을 계산합니다. 프로젝트에서 AI 담당자는 데이터·모델 가능성을 확인하고, 결과·실패 조건·입력/출력·실행 방법을 팀에 설명합니다.

### 시작하기

[실행 환경](docs/runtime.md)을 준비한 뒤 [1주차 목표](week1/README.md)와 [실습 노트북](week1/week1_mission.ipynb)을 확인해주세요. HINT와 채점머신은 노트북에 함께 들어 있습니다.

주차 흐름은 [기존 AI 개편안](https://app.notion.com/p/3e93f155920280a79058d2b0e62bf233#3e93f15592028020b0cafe5d7524ab51)을 따릅니다.
