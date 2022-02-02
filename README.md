# -[데이콘] KNOW기반 직업 추천 알고리즘 경진대회-

대회 기간 : 2021년 12월 06일 ~ 2022년 1월 28일
대회 개요 : KNOW(한국직업정보) 데이터를 기반으로 직업추천 모델을 만들어보고 직업과 연관성 높은 직무능력을 탐색 및 발굴
대회 목적 : KNOW(한국직업정보) 설문 데이터셋을 활용한 직업 추천 알고리즘 개발

# Data 설명 
(1) 2017_KNOW_재직자조사_설문지
(2) 2018_KNOW_재직자조사_설문지
(3) 2019_KNOW_재직자조사_설문지
(4) 2020_KNOW_재직자조사_설문지
대략 150개의 설문 문항 중 선택형, 서술형 문항이 혼재되어 있음

# 데이터 전처리 
결측치 및 오류 데이터 처리
주요 결측치 문항별 최빈값으로 대체함(data leakage를 고려하여 test 데이터 결측치는 train 데이터의 통계량 이용)

# Feature Engineering
서술형 문항에 대해서 원핫 인코딩 처리를 해줌
수 많은 서술형 문항을 일일히 원핫 인코딩으로 변경해주는 것이 비효율적이라고 판단하여 SentenceBERT를 사용해봄
SentenceBERT를 사용하여 각 서술형 문항을 Clustering 시도, 그러나 원핫 인코딩을 직접 해주었을 경우 성능이 더 좋게 나타남
원핫 인코딩 실행 : Public 점수 0.70555, SentenceBERT 실행 : 0.69564

# 모델 선택
분류에 사용되는 주요 머신러닝 모델 XGBoost, LightGBM, RandomForest, DecisionTree, SVM 등 비교 결과 RandomForest 모델이 우수하여 이를 채택함

# 최종 결과 
macro-f1 score : 0.70539 (10/360)
