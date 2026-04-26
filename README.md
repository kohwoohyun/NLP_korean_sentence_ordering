# 한국어 문장 순서 예측 (Korean Sentence Ordering)

## 프로젝트 개요

DACON '문맥 기반 문장 순서 예측 AI 경진대회'
(종료된 대회) 를 기반으로 한 NLP 학습 프로젝트입니다.

해당 대회 관련 정보나 데이터는 
[문맥 기반 문장 순서 예측 AI 경진대회](https://dacon.io/competitions/official/236489/overview/description)를 통해 확인할 수 있습니다.

뒤섞인 4개의 한국어 문장을 올바른 순서로
배열하는 AI 알고리즘을 개발했습니다.

단순 성능 극대화보다 다양한 접근법을 비교하고
각 방법의 원리를 분석하는 데 초점을 맞췄습니다.

- 환경: Google Colab Pro (A100) + DGX Spark (128GB)
- 사용 모델: kogpt2, kanana-2.1b, polyglot-3.8b,
             Qwen3-4B, Qwen3-14B
  
## 접근 방식

총 3단계로 실험을 진행했습니다.

### Stage 1 — PPL 기반 베이스라인
파인튜닝 없이 사전학습 모델의 Perplexity를 활용했습니다.
4개 문장의 24가지 순열 중 PPL이 가장 낮은 순서를
정답으로 예측합니다.

코드는 [Stage1](./Stage1)을 통해 확인할 수 있습니다.

### Stage 2 — PPL 원리 검증 + 데이터 증강
PPL 방식이 실제로 동작하는 이유를 수치로 검증하고
파인튜닝을 위한 증강 데이터를 생성했습니다.

코드는 [Stage2](./Stage2)을 통해 확인할 수 있습니다.

### Stage 3 — QLoRA 파인튜닝
문장 순서 태스크를 직접 학습시키는 방식으로
Stage 1의 PPL 방식과 성능을 비교했습니다.

코드는 [Stage3](./Stage3)을 통해 확인할 수 있습니다.
