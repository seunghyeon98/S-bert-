# Food recommendation system with S-BERT


## Abstract

## Pipeline
![image](https://user-images.githubusercontent.com/111716640/233542322-0e322a80-7d49-47ed-a569-eb7050236a96.png)


## Dataset
![image](https://github.com/seunghyeon98/S-bert-/assets/111716640/2318e3fd-fbed-49fc-b9d4-a81c4a30f792)

음식의 레시피에 대한 데이터는 농식품올바로의 메뉴젠을 통해 수집하였습니다.


## Model
* S-bert [ko-sroberta-multitask]
![image](https://github.com/seunghyeon98/S-bert-/assets/111716640/5b58db62-f853-4e79-8f01-89a39f102a97)

S-bert 를 통하여 [food, ingredient1, ingredient2,...] 형식으로 음식 이름과 해당 레시피에 사용된 재료들을 
한 문장으로 데이터를 구성하였습니다.

구성한 문장은 S-bert 모델을 통해 sentence -> vector 로 임베딩을 진행합니다.

* K-Means

벡터화된 각 문장들은 K-means를 통하여 클러스터를 이루게 되고,
K-means를 통해 음식이 어떤 분류에 속하는지 알 수 있게 됩니다.
각 클러스터들을 통해 음식들이 반찬,메인요리,해산물 요리,국,... 등등 으로 나뉘게 됩니다.


* Recommendation

입력값으로 먹은 음식의 이름을 넣으면, 해당 음식과 재료가 겹치지 않는 선에서
각 클러스터별로 음식을 추천하게 됩니다.



## Reference
http://koreanfood.rda.go.kr/main

https://huggingface.co/jhgan/ko-sroberta-multitask
