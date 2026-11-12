# Week 3

이번 주차에는 이미 학습된 **BERT의 구조**를 살펴보고, 외부 문서를 검색해 답변하는 **RAG**를 실습합니다.

> **📌  이번 실습은 가급적이면 Google Colab에서 진행해주세요!**

> 노트북을 실행하기 전에 런타임 유형을 **T4 GPU**로 바꿔주세요.

### 이번 주차의 학습 목표

- 사전학습 모델의 개념 이해
- BERT 모델의 구조 이해
- RAG의 전체 흐름 이해
- Fine-Tuning과 RAG의 차이 이해

### Mission

[실습 노트북](week3_mission.ipynb)의 안내에 따라 필요한 이론을 살펴보고 핵심 코드를 작성합니다.

개념 정리와 생각해보기는 노트북의 답변 셀에 작성해주세요.

- **Mission1 (BERT)**: 사전학습 모델을 불러와 tokenizer, Embedding, Attention, Pooler 등 BERT의 구조를 모델 출력과 연결해 살펴봅니다. 실제 파인튜닝 학습은 Week4에서 진행합니다.
- **Mission2 (RAG)**: 배송/환불 정책 문서를 검색해 답변하는 RAG를 만들고, RAG를 사용했을 때와 사용하지 않았을 때의 답변을 비교합니다.

결과 해석은 실제 출력에 근거해 작성해주세요.
(이번 주차는 이전 주차의 결과 파일이 필요하지 않습니다.)

### 실행 전 확인

- **Colab**: 노트북의 설치 셀에서 Colab용 `%pip install` 줄의 주석을 해제해 실행해주세요.
- **로컬**: `transformers`와 `torch`는 `uv sync --locked`로 설치됩니다. RAG에 필요한 `sentence-transformers`와 `faiss-cpu`는 노트북의 uv 설치 셀로 설치됩니다.
- 모델 파일은 처음 불러올 때 내려받습니다. `klue/bert-base`는 약 440MB, `Qwen/Qwen2.5-3B-Instruct`는 약 6.2GB입니다.

### 실습 관련 보충자료

| 자료 | 참고할 내용 | 읽을 부분 |
|---|---|---|
| [GDG 홍익대학교: Introduction To Attention Algorithm](https://www.youtube.com/watch?v=7LVRciBEGaM) | Attention 개념을 설명하는 세미나 | 영상 전체 |
| [테디노트: RAG의 동작 과정 쉽게 이해하기 EP01](https://www.youtube.com/watch?v=zybyszetEcE) | RAG 개념과 데이터 전처리 과정 | 4분 54초까지 RAG의 기본 개념을 설명하고, 이후에는 구체적인 전처리 과정을 설명하니 필요한 부분을 골라 들어보세요. |
| [Hugging Face: 토크나이저](https://huggingface.co/learn/llm-course/ko/chapter2/4) | 문장을 토큰과 숫자로 바꾸는 과정 | 서브워드 토큰화 & 토큰에서 입력 ID까지 |
| [Hugging Face: 모델](https://huggingface.co/learn/llm-course/ko/chapter2/3) | 사전학습 모델을 불러오고 입력을 넣는 방법 | Different loading methods & Using a Transformer model for inference |

### 더 공부하고 싶다면

| 자료 | 참고할 내용 | 읽을 부분 |
|---|---|---|
| [BERT 논문](https://arxiv.org/abs/1810.04805) | BERT의 제안 배경과 구조 | 초록 |
| [RAG 논문](https://arxiv.org/abs/2005.11401) | RAG의 제안 배경과 구조 | 초록 |
| [테디노트: <랭체인LangChain 노트>](https://wikidocs.net/book/14314) | LangChain으로 RAG를 구현하는 방법 | 필요한 부분을 골라 읽어보세요! |
| [테디노트: langchain-kr GitHub](https://github.com/teddylee777/langchain-kr) | LangChain 한국어 튜토리얼 예제 코드 | 필요한 부분을 골라 살펴보세요! |
| [3Blue1Brown: 트랜스포머, ChatGPT가 트랜스포머로 만들어졌죠. - DL5](https://youtu.be/g38aoGttLhI) | Transformer의 전체 구조 | 영상 전체 |
| [3Blue1Brown: 그 이름도 유명한 어텐션, 이 영상만 보면 이해 완료! - DL6](https://youtu.be/_Z3rXeJahMs) | 단어 벡터가 문맥에 따라 바뀌는 과정을 시각적으로 이해하기 | 영상 전체 |

전체 흐름은 [코스 개요](../README.md), 로컬 또는 Colab 설정은 [별도 실행 안내](../docs/runtime.md)를 확인해주세요.
