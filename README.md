![IMG_0269](https://user-images.githubusercontent.com/48639017/147466091-97ed72bc-5a28-4258-8616-13fe49549926.jpg)

---

## ๐ก ์ฐ ์ถ์ฒ ์๋น์ค



<img src = https://user-images.githubusercontent.com/57916633/147496793-014c86a8-3b80-46d4-81ce-45b36587e7ea.png width = 250 height = 400  style="padding: 0;margin:0;">





---

# Contentsโฐ

1. [ํ๋ก์ ํธ ์๊ฐ](#ํ๋ก์ ํธ-์๊ฐ)
    - ๋๊ธฐ ๋ฐ ๋ชฉํ
    - ๋ฐ์ดํฐ
2. [๋ฐ์ดํฐ ์ ์ฒ๋ฆฌ](#๋ฐ์ดํฐ-์ ์ฒ๋ฆฌ)
    - ์ฃผ์ ๋ด์ฉ
3. [๋ชจ๋ธ๋ง](#๋ชจ๋ธ๋ง)
    - ๋ชจ๋ธ ์ ํ
    - ๋ชจ๋ธ ์ฑ๋ฅ ํ๊ฐ
4. [๋ชจ๋ธ ์์ธก ๊ฒฐ๊ณผ](#๋ชจ๋ธ-์์ธก-๊ฒฐ๊ณผ)
    - ์์ธก ๊ฒฐ๊ณผ ๋ฐ ํ๊ฐ
    - ์ถ์ฒ ์๋น์ค
5. [๊ฒฐ๋ก ](#๊ฒฐ๋ก )
    - ํ๊ณ์ 
    - ๊ฐ์ ์ 
---
    

# ํ๋ก์ ํธ ์๊ฐ

### ๋๊ธฐ ๋ฐ ๋ชฉํ
๐ก ๋๊ธฐ
- ์ฝ๋ก๋๋ก ์ธํด ์ผ์ธ ํ๋ ์ธ๊ตฌ๊ฐ ์ฆ๊ฐํ๋ฉฐ ๋ฑ์ฐ์ ์ธ๊ธฐ๋ ์์น
- ์ ๊ตญ์ ์ผ๋ก 100๋ ๋ณ์ฐ์ด ๋ถํฌ๋์ด ์์ผ๋ ์ถ์ฒ ์ง์ญ์ ๋์ฒด๋ก ์์ธ์ ํ์ 

๐ก ๋ชฉํ
- 100๋ ๋ช์ฐ๊ณผ ์ ์ฌํ ์ฐ ์ถ์ฒ

### ์ํ ๊ธฐ๊ฐ ๋ฐ ํ์
๐ก ๊ธฐ๊ฐ
- 2021-12-07 ~ 2021-12-21

๐ก ํ์
- ์ค์๋ฏผ
- ํ์ฑ๋ฏธ


### ๋ฐ์ดํฐ
![unknown](https://user-images.githubusercontent.com/48639017/147468962-d33b46ca-88d2-49bd-874e-aa0560f34a97.png)

    

# ๋ฐ์ดํฐ ์ ์ฒ๋ฆฌ
### ์ฃผ์ ๋ด์ฉ
1. Data Extraction
    - Raw data
        - 2500์ฌ๊ฐ์ ์ฐ ๋ฐ์ดํฐ (Json)
        - ์ฐ ์ ๋ณด ๊ฒ์ API
    - Json, API ๋ฑ์์ Data ์ถ์ถ
        - ๊ฐ ์ฐ๋ค์ ๊ตฌ๋ณํ  ์ ์๋ ์ ๋ณด์ ์์นํ ๋ฐ์ดํฐ๋ฅผ ์ ํํด ์ถ์ถ
            - ์ฐ์ ์ด๋ฆ
            - ์ฐ์ ์ฝ๋ ๋ฒํธ
            - ์ฐ์ ์์ฌ์ง
            - ์ฐ์ ๋์ด
            - ๋ฑ์ฐ๋ก ๊ธธ์ด์ ํฉ
            - API ์ฐ ์ ๋ณด ๊ฒ์ ๊ฒฐ๊ณผ
    - Crawling์ ํตํด ๊ฒฐ์ธก์น ๋ณด์(์ฐ์ ๋์ด, API ๊ฒ์ ๊ฒฐ๊ณผ)
    
2. ์์ฐ์ด ์ฒ๋ฆฌ
    - 100๋ ๋ช์ฐ api ๊ฒ์ ๊ฒฐ๊ณผ์์ Konlpy - KKMA ํ์ฉ ๋ช์ฌ ์ถ์ถ
    - CountVectorizer ํ์ Raw, Selected ๋ง๋ญ์น ์ถ์ถ
        - Raw : 100๋ ๋ช์ฐ ๊ฒ์ ๊ฒฐ๊ณผ์ ๋ชจ๋  ๋ช์ฌ
        - Selected : ๊ฒ์ ๊ฒฐ๊ณผ ์ค ๋น๋์ 100ํ ์ด์์ด๊ฑฐ๋ ํต์ฌ์ด๋ผ๊ณ  ์๊ฐ๋๋ ๋ช์ฌ
    - Cosine Similarity ๊ณ์ฐ
        - ๋ง๋ญ์น ๋ฒกํฐํ - OneHot Encoding
        - ๋ง๋ญ์น ๋ฒกํฐ์ ๋ชจ๋  ์ฐ ๋ฐ์ดํฐ ์ ์ฌ๋ ์ธก์ 
    
    <img width="1017" alt="Screen Shot 2022-01-03 at 4 12 06 PM" src="https://user-images.githubusercontent.com/48639017/147906587-4f17763e-d701-4d86-a814-6d3265499239.png">
    <p align='center'>
    <์ข: Raw ๋ง๋ญ์น / ์ฐ: Selected ๋ง๋ญ์น>
    </p>

3. ์ ์ฒด ์ฐ ํ๋์ row๋ก ๋ฐ์ดํฐํ๋ ์ ์์ฑ

    ![1](https://user-images.githubusercontent.com/48639017/147469557-fadf47e7-1c0c-4961-b9d8-44dfd193d338.png)

    - MNTN_CODE : ์ฐ ๊ณ ์  ์ฝ๋
    - MNTN_NM : ์ฐ ์ด๋ฆ
    - MNTN_LOC : ์ฐ ์์ฌ์ง
    - MNTN_HEIGHT : ์ฐ ๋์ด
    - ROAD_EASY/MID/DIFF : ๋์ด๋ ๋ณ ๋ฑ์ฐ๋ก ๊ธธ์ด
    - ROAD_SUM : ์ฐ์ ์ด ๋ฑ์ฐ๋ก ๊ธธ์ด
    - MNTN_RES : ์ฐ ์ ๋ณด api ๊ฒ์ ๊ฒฐ๊ณผ
    - Sel_Cos, Raw_Cos : 100๋ ๋ช์ฐ๊ณผ์ ์ฝ์ฌ์ธ ์ ์ฌ๋ ๊ฐ
    
4. Train, Test data set
    - All : Object Type Feature ์ ์ธ
    
        <img src =https://user-images.githubusercontent.com/57916633/147900410-ba0cb4f1-7b9a-4ab6-bbca-0c0fe069bf35.png width = 600 height = 450>


    - ROAD_SUM
        - ROAD_EASY์์ ์๊ด๊ด๊ณ๊ฐ 1์ด๋ฉฐ ๊ฑฐ์ ์ ์ฌํ ๋ถํฌ๋ฅผ ๋ณด์ธ๋ค
        - ๋๋ฌธ์ ์ข์๊ด๊ณ๊ฐ ์กด์ฌํ๊ฑฐ๋ ์ ์๋ฏธํ ์งํ๊ฐ ๋์ง ์์ ๊ฒ์ด๋ผ ์๊ฐํ์ฌ ์ ์ธ
 
 
    ![image](https://user-images.githubusercontent.com/57916633/147900308-e067a859-3cae-4b8a-a491-eac43d19eb64.png)

    - Train : 100๋ ๋ช์ฐ + ์ฐ์ผ๋ก ๋ถ๋ฅํ์ง ์์ ๋ฐ์ดํฐ
    - Test : ์ฐ์ผ๋ก ๋ถ๋ฅ๋ ๋ฐ์ดํฐ - 100๋ ๋ช์ฐ
    
5. Data set Label Imbalanced
    - Label์ 0์ด 1๋ณด๋ค 3๋ฐฐ ์ด์ ๋ง์ ์ ํํ ํ์ต์ด ์ด๋ฃจ์ด์ง์ง ์์๋ค
    - SMOTE๋ฅผ ์ฌ์ฉํ Label ๋ถ๊ท ํ ํด๊ฒฐ 
        - SMOTE : Label์ด 1์ธ ๋ฐ์ดํฐ๋ค๊ณผ ์ ์ฌํ ์๋ก์ด ๋ฐ์ดํฐ๋ฅผ ์์ฑํ์ฌ Label ๋ถ๊ท ํ์ ํด์ํ๋ ๊ธฐ๋ฒ
    
    ![2](https://user-images.githubusercontent.com/48639017/147471604-d7a4bd9f-3380-4622-9f10-fe707c4e1482.png)

6. Scaling
    - Feature๋ค์ ๋ถํฌ๋ฅผ ์๊ฐ์ ์ผ๋ก ํ์ธํ๊ธฐ ์ํด์ Scaler ์ ์ฉ 
    - StandardScaler ์ ์ฉ 
    - ์ด์์น๊ฐ ๋ง์ง ์๊ณ , ์ด์์น๊ฐ ๊ทธ๋๋ก ๋ณด์กด๋  ํ์๊ฐ ์์ด์  Robust ๋ Minmax๊ฐ ์๋ Standard Scaler๋ฅผ ์ ์ฉ
    
    ![](https://cdn.discordapp.com/attachments/900310026793652244/925002953985773618/unknown.png)
    

# ๋ชจ๋ธ๋ง
### ๋ชจ๋ธ ์ ํ
- ํ์ดํ๋ผ์ธ ๊ตฌ์ถ ๋ฐ ์ต์ ์ ๋ชจ๋ธ ๋์ถ
    - ํ์ดํ๋ผ์ธ GridSearchCV ๊ฑฐ์ณ ์ด 5๊ฐ์ง classifier ๋ชจ๋ธ ์ค ์ ํ
    - RandaomForestClassifier ์ ํ
    
    <img width="523" alt="Screen Shot 2021-12-28 at 10 12 02 AM" src="https://user-images.githubusercontent.com/48639017/147517136-64a5a368-8ae5-4221-9e9f-75f5b68d881f.png">

### ๋ชจ๋ธ ์ฑ๋ฅ ํ๊ฐ
- K-fold cross validation ํ์ฌ ์ฑ๋ฅ ํ๊ฐ
    - accuracy, precision, recall
    
    ![score](https://user-images.githubusercontent.com/48639017/147516963-c8f51986-18d6-4890-b1b7-db25098642c8.png)

# ๋ชจ๋ธ ์์ธก ๊ฒฐ๊ณผ
### ์์ธก ๊ฒฐ๊ณผ
- train-test class scatter
    ![res](https://user-images.githubusercontent.com/48639017/147474227-590f26c6-4fa9-461a-925b-d01ed3feed71.png)
- test ๋ฐ์ดํฐ ์ ์ค ์ข์ ์ฐ์ผ๋ก ๋ถ๋ฅ๋ ์ฐ ์ด 493๊ฐ

### ์์ธก ํ๊ฐ
- ์ข๊ฒ ๋ถ๋ฅ๋ 493๊ฐ ์ค ๋ธ๋์ผํฌ ์ํ์ธ ํด๋ฝ 100+ ๋ช์ฐ 55๊ฐ ํฌํจ
- ์ข๊ฒ ๋ถ๋ฅ๋ 493๊ฐ ์ค ๋๋ค ์ถ์ถ ํ ์ ์ฑ์  ํ๊ฐ
    - ๋๋ค ์ถ์ถ ๋ ์ฐ์ ๊ฒ์ ๊ฒฐ๊ณผ
    - ๊ฒ์ ๊ฒฐ๊ณผ์ค 100๋ ๋ช์ฐ์ ์ ์  ๊ธฐ์ค์ ํด๋นํ๋ ์ญ์ฌ์  ์ฌ์ค, ๊ฒฝ๊ด ๋ฑ ์ค์ ์์ธ์ด ํ์ธ ๋์๋ค.
    
![image](https://user-images.githubusercontent.com/57916633/147902083-8879abaf-c266-4e76-ad00-231a27e01b80.png)


### ๐ก ์ถ์ฒ ์๋น์ค
- ์ฌ์ฉ์ ํฌ๋ง ์ง์ญ ์ ํ ํ ์ข์ ์ฐ top 5 ์ถ์ฒ
    - Class 1๋ก ์์ธกํ  proba ๊ฐ ๊ธฐ์ค ๋์ ์์ผ๋ก ์ถ์ฒ

    <img src = https://user-images.githubusercontent.com/57916633/147496793-014c86a8-3b80-46d4-81ce-45b36587e7ea.png width = 250 height = 400>

- Demo Code 
    ![image](https://user-images.githubusercontent.com/57916633/147901469-b4b894d2-2cc9-483b-98da-3920e4e54ea0.png)
    
    - ์์ธก๋ ๊ฒฐ๊ณผ Data set์ ์ข์ ์ฐ์ผ๋ก ๋ถ๋ฅ๋  ํ๋ฅ  ๊ฐ (Prob_1) ์ ๊ธฐ์ค์ผ๋ก ์ ๋ ฌ
    - ์ฌ์ฉ์๊ฐ ์กฐํํ๊ณ  ์ถ์ ์ง์ญ์ ๊ฒฐ๊ณผ์ค TOP 5๋ฅผ ์ถ๋ ฅ
    

    
# ๊ฒฐ๋ก 
### ํ๊ณ์ 
- open Api
    - ํต์ผ๋์ง ์์์ฑ ๊ด๋ฆฌ๋๊ณ , ๋ชจ๋  ๋ฐ์ดํฐ๋ฅผ ํฌํจํ์ง ์์
- ์ ์ฑ์  ํ๊ฐ ๋ฐฉ๋ฒ
    - ๋ชจ๋ธ ์ฑ๋ฅ ๋น๊ต ๋ถ๊ฐ๋ฅ

### ๊ฐ์ ์ 
- ์์ฐ์ด ์ฒ๋ฆฌ
    - onehot-encoding์ ํ๊ณ์ ์ผ๋ก ๋ฌธ์ฅ๊ฐ ์ ์ฌ๋ ํ์ ์ด๋ ค์
    - tf-idf ํ์ฉ ํ ์ ์ฌ๋ ๋์ถ๋ก ๊ฐ์  ๊ฐ๋ฅ
    - Sel_Cos ์ ๋ฌด์ ๋ค๋ฅธ ์์ธก ๋ถํฌ ์ฐจ์ด ์์ธ ํ์
    
    ![compare](https://user-images.githubusercontent.com/48639017/147475344-bfa67056-155a-4494-8e98-8ab0e3796155.png)




---

### ์ฐธ๊ณ 
[๋ฑ์ฐ๋ก ์ ๋ณด ๋ฐ์ดํฐ](https://www.forest.go.kr/kfsweb/kfi/kfs/trail/trailInformation.do?pblicDataId=PBD0000041&tabs=3&mn=NKFS_06_08_02&subTitle=%EB%93%B1%EC%82%B0%EB%A1%9C%EC%A0%95%EB%B3%B4)

[๋ช์ฐ ๋ฑ์ฐ๋ก ๋ฐ์ดํฐ](https://www.forest.go.kr/kfsweb/kfi/kfs/nwopapi/gdTrailInformation.do?pblicDataId=PBD0000021&tabs=3&mn=NKFS_06_08_02&subTitle=%EB%AA%85%EC%82%B0%EB%93%B1%EC%82%B0%EB%A1%9C)

[์ฐ์ ๋ณด ๋ฐ์ดํฐ](https://www.forest.go.kr/kfsweb/kfi/kfs/nwopapi/gdTrailInformation.do?pblicDataId=PBD0000021&tabs=3&mn=NKFS_06_08_02&subTitle=%EB%AA%85%EC%82%B0%EB%93%B1%EC%82%B0%EB%A1%9C)

---

### ๊ฐ๋ฐํ๊ฒฝ ๐ป
- Python >= 3.8 version
- Scikit-learn >= 0.24 version
- Konlpy == 0.5.2 version


---

### ์ฌ์ฉ ๊ธฐ์  ์คํ ๐ ๏ธ
- Python
- Scikit-learn
- Konlpy
- Pandas
- Seaborn
- Git


<img src = https://user-images.githubusercontent.com/57916633/147529037-db3e9310-5690-4155-b2d5-2554eb294bf6.png width = '950' height='350'>

