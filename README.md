![IMG_0269](https://user-images.githubusercontent.com/48639017/147466091-97ed72bc-5a28-4258-8616-13fe49549926.jpg)

---

## 💡 산 추천 서비스



<img src = https://user-images.githubusercontent.com/57916633/147496793-014c86a8-3b80-46d4-81ce-45b36587e7ea.png width = 250 height = 400  style="padding: 0;margin:0;">





---

# Contents⛰

1. [프로젝트 소개](#프로젝트-소개)
    - 동기 및 목표
    - 데이터
2. [데이터 전처리](#데이터-전처리)
    - 주요 내용
3. [모델링](#모델링)
    - 모델 선택
    - 모델 성능 평가
4. [모델 예측 결과](#모델-예측-결과)
    - 예측 결과 및 평가
    - 추천 서비스
5. [결론](#결론)
    - 한계점
    - 개선점
---
    

# 프로젝트 소개

### 동기 및 목표
💡 동기
- 코로나로 인해 야외 활동 인구가 증가하며 등산의 인기도 상승
- 전국적으로 100대 병산이 분포되어 있으나 추천 지역은 대체로 서울에 한정

💡 목표
- 100대 명산과 유사한 산 추천

### 수행 기간 및 팀원
💡 기간
- 2021-12-07 ~ 2021-12-21

💡 팀원
- 윤영민
- 홍성미


### 데이터
![unknown](https://user-images.githubusercontent.com/48639017/147468962-d33b46ca-88d2-49bd-874e-aa0560f34a97.png)

    

# 데이터 전처리
### 주요 내용
1. Data Extraction
    - Raw data
        - 2500여개의 산 데이터 (Json)
        - 산 정보 검색 API
    - Json, API 등에서 Data 추출
        - 각 산들을 구별할 수 있는 정보와 수치형 데이터를 선택해 추출
            - 산의 이름
            - 산의 코드 번호
            - 산의 소재지
            - 산의 높이
            - 등산로 길이의 합
            - API 산 정보 검색 결과
    - Crawling을 통해 결측치 보완(산의 높이, API 검색 결과)
    
2. 자연어 처리
    - 100대 명산 api 검색 결과에서 Konlpy - KKMA 활용 명사 추출
    - CountVectorizer 후에 Raw, Selected 말뭉치 추출
        - Raw : 100대 명산 검색 결과의 모든 명사
        - Selected : 검색 결과 중 빈도수 100회 이상이거나 핵심이라고 생각되는 명사
    - Cosine Similarity 계산
        - 말뭉치 벡터화 - OneHot Encoding
        - 말뭉치 벡터와 모든 산 데이터 유사도 측정
    
    <img width="1017" alt="Screen Shot 2022-01-03 at 4 12 06 PM" src="https://user-images.githubusercontent.com/48639017/147906587-4f17763e-d701-4d86-a814-6d3265499239.png">
    <p align='center'>
    <좌: Raw 말뭉치 / 우: Selected 말뭉치>
    </p>

3. 전체 산 하나의 row로 데이터프레임 생성

    ![1](https://user-images.githubusercontent.com/48639017/147469557-fadf47e7-1c0c-4961-b9d8-44dfd193d338.png)

    - MNTN_CODE : 산 고유 코드
    - MNTN_NM : 산 이름
    - MNTN_LOC : 산 소재지
    - MNTN_HEIGHT : 산 높이
    - ROAD_EASY/MID/DIFF : 난이도 별 등산로 길이
    - ROAD_SUM : 산의 총 등산로 길이
    - MNTN_RES : 산 정보 api 검색 결과
    - Sel_Cos, Raw_Cos : 100대 명산과의 코사인 유사도 값
    
4. Train, Test data set
    - All : Object Type Feature 제외
    
        <img src =https://user-images.githubusercontent.com/57916633/147900410-ba0cb4f1-7b9a-4ab6-bbca-0c0fe069bf35.png width = 600 height = 450>


    - ROAD_SUM
        - ROAD_EASY와의 상관관계가 1이며 거의 유사한 분포를 보인다
        - 때문에 종속관계가 존재하거나 유의미한 지표가 되지 않을 것이라 생각하여 제외
 
 
    ![image](https://user-images.githubusercontent.com/57916633/147900308-e067a859-3cae-4b8a-a491-eac43d19eb64.png)

    - Train : 100대 명산 + 산으로 분류하지 않은 데이터
    - Test : 산으로 분류된 데이터 - 100대 명산
    
5. Data set Label Imbalanced
    - Label의 0이 1보다 3배 이상 많아 정확한 학습이 이루어지지 않았다
    - SMOTE를 사용한 Label 불균형 해결 
        - SMOTE : Label이 1인 데이터들과 유사한 새로운 데이터를 생성하여 Label 불균형을 해소하는 기법
    
    ![2](https://user-images.githubusercontent.com/48639017/147471604-d7a4bd9f-3380-4622-9f10-fe707c4e1482.png)

6. Scaling
    - Feature들의 분포를 시각적으로 확인하기 위해서 Scaler 적용 
    - StandardScaler 적용 
    - 이상치가 많지 않고, 이상치가 그대로 보존될 필요가 있어서  Robust 나 Minmax가 아닌 Standard Scaler를 적용
    
    ![](https://cdn.discordapp.com/attachments/900310026793652244/925002953985773618/unknown.png)
    

# 모델링
### 모델 선택
- 파이프라인 구축 및 최적의 모델 도출
    - 파이프라인 GridSearchCV 거쳐 총 5가지 classifier 모델 중 선택
    - RandaomForestClassifier 선택
    
    <img width="523" alt="Screen Shot 2021-12-28 at 10 12 02 AM" src="https://user-images.githubusercontent.com/48639017/147517136-64a5a368-8ae5-4221-9e9f-75f5b68d881f.png">

### 모델 성능 평가
- K-fold cross validation 하여 성능 평가
    - accuracy, precision, recall
    
    ![score](https://user-images.githubusercontent.com/48639017/147516963-c8f51986-18d6-4890-b1b7-db25098642c8.png)

# 모델 예측 결과
### 예측 결과
- train-test class scatter
    ![res](https://user-images.githubusercontent.com/48639017/147474227-590f26c6-4fa9-461a-925b-d01ed3feed71.png)
- test 데이터 셋 중 좋은 산으로 분류된 산 총 493개

### 예측 평가
- 좋게 분류된 493개 중 블랙야크 알파인 클럽 100+ 명산 55개 포함
- 좋게 분류된 493개 중 랜덤 추출 후 정성적 평가
    - 랜덤 추출 된 산의 검색 결과
    - 검색 결과중 100대 명산의 선정 기준에 해당하는 역사적 사실, 경관 등 중요 요인이 확인 되었다.
    
![image](https://user-images.githubusercontent.com/57916633/147902083-8879abaf-c266-4e76-ad00-231a27e01b80.png)


### 💡 추천 서비스
- 사용자 희망 지역 선택 후 좋은 산 top 5 추천
    - Class 1로 예측할 proba 값 기준 높은 순으로 추천

    <img src = https://user-images.githubusercontent.com/57916633/147496793-014c86a8-3b80-46d4-81ce-45b36587e7ea.png width = 250 height = 400>

- Demo Code 
    ![image](https://user-images.githubusercontent.com/57916633/147901469-b4b894d2-2cc9-483b-98da-3920e4e54ea0.png)
    
    - 예측된 결과 Data set을 좋은 산으로 분류될 확률 값 (Prob_1) 을 기준으로 정렬
    - 사용자가 조회하고 싶은 지역의 결과중 TOP 5를 출력
    

    
# 결론
### 한계점
- open Api
    - 통일되지 않은채 관리되고, 모든 데이터를 포함하지 않음
- 정성적 평가 방법
    - 모델 성능 비교 불가능

### 개선점
- 자연어 처리
    - onehot-encoding의 한계점으로 문장간 유사도 파악 어려움
    - tf-idf 활용 후 유사도 도출로 개선 가능
    - Sel_Cos 유무에 다른 예측 분포 차이 원인 파악
    
    ![compare](https://user-images.githubusercontent.com/48639017/147475344-bfa67056-155a-4494-8e98-8ab0e3796155.png)




---

### 참고
[등산로 정보 데이터](https://www.forest.go.kr/kfsweb/kfi/kfs/trail/trailInformation.do?pblicDataId=PBD0000041&tabs=3&mn=NKFS_06_08_02&subTitle=%EB%93%B1%EC%82%B0%EB%A1%9C%EC%A0%95%EB%B3%B4)

[명산 등산로 데이터](https://www.forest.go.kr/kfsweb/kfi/kfs/nwopapi/gdTrailInformation.do?pblicDataId=PBD0000021&tabs=3&mn=NKFS_06_08_02&subTitle=%EB%AA%85%EC%82%B0%EB%93%B1%EC%82%B0%EB%A1%9C)

[산정보 데이터](https://www.forest.go.kr/kfsweb/kfi/kfs/nwopapi/gdTrailInformation.do?pblicDataId=PBD0000021&tabs=3&mn=NKFS_06_08_02&subTitle=%EB%AA%85%EC%82%B0%EB%93%B1%EC%82%B0%EB%A1%9C)

---

### 개발환경 💻
- Python >= 3.8 version
- Scikit-learn >= 0.24 version
- Konlpy == 0.5.2 version


---

### 사용 기술 스택 🛠️
- Python
- Scikit-learn
- Konlpy
- Pandas
- Seaborn
- Git


<img src = https://user-images.githubusercontent.com/57916633/147529037-db3e9310-5690-4155-b2d5-2554eb294bf6.png width = '950' height='350'>

