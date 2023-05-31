# S-BERT 기반 음식 및 식재료 임베딩 및 클러스터링을 활용한 음식 다양성 추천 시스템



## Pipeline & Abstract

![image](https://github.com/seunghyeon98/S-bert-/assets/111716640/6565de38-186d-40cc-8420-1ede400d2f20)



### Abstract
레시피 데이터를 이용하여 임베딩과 클러스터링 기법을 적용하여 데이터 셋에 대한 그룹화를 진행하여 다양한 추천을 가능하게 한다.

## Dataset
![image](https://github.com/seunghyeon98/S-bert-/assets/111716640/2318e3fd-fbed-49fc-b9d4-a81c4a30f792)

농촌진흥청 국립농업과학원에서 제공한 공공데이터포털의 농식품 식단관리 (메뉴젠) 음식 및 재료 정보 데이터를 가공하여 사용하였습니다.


## Model
* S-bert [ko-sroberta-multitask]
![image](https://github.com/seunghyeon98/S-bert-/assets/111716640/5b58db62-f853-4e79-8f01-89a39f102a97)

S-bert 를 통하여 [food, ingredient1, ingredient2,...] 형식으로 음식 이름과 해당 레시피에 사용된 재료들을 
한 문장으로 데이터를 구성하였습니다.

구성한 문장은 S-bert 모델을 통해 sentence -> vector 로 임베딩을 진행합니다.

* K-Means
![image](https://github.com/seunghyeon98/S-bert-/assets/111716640/ce091453-fa4f-491c-8797-d1828773eb10)

벡터화된 각 문장들은 K-means를 통하여 클러스터를 이루게 되고,
K-means를 통해 음식이 어떤 분류에 속하는지 알 수 있게 됩니다.
각 클러스터들을 통해 음식들이 반찬,메인요리,해산물 요리,국,... 등등 으로 나뉘게 됩니다.


* Recommendation

![image](https://github.com/seunghyeon98/S-bert-/assets/111716640/a47dc0e4-5857-450c-a332-268de30280ca)

사용자가 직전에 소비한 음식을 입력값 (Query)을 받습니다.

Query의 음식 재료와 Dataset에 있는 음식의 재료를 교집합의 갯수로 비교하여 
재료가 겹치지 않는 선에서 음식 추천을 제안합니다.

![image](https://github.com/seunghyeon98/S-bert-/assets/111716640/af16b9cf-4cb9-4ef9-b936-9ad50d81cd86)
[직전에 먹은 음식이 파전이라면 해당 음식을 제안합니다]


## Reference
[http://koreanfood.rda.go.kr/main](https://www.data.go.kr/data/15081026/openapi.do)

https://huggingface.co/jhgan/ko-sroberta-multitask
