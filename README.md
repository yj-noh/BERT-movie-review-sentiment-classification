# BERT-movie-review-sentiment-classification

**1.	데이터셋** \
Naver sentiment movie corpus (rating_train.txt, rating_test.txt) 데이터 셋을 사용하였으며, rating_train.txt를 사용하여 모델 생성 후 rating_test.txt를 사용하여 예측 수행하였다. Train data는 15만개, Test data는 5만개의 리뷰로 이루어져 있다.

**2.	사용 모델 및 하이퍼 파라미터**\n
104개의 언어로 된 말뭉치로 사전 학습한 모델인 BERT-multilingual과 SKTBrain에서 개발한 한국어에 특화된 KoBERT 모델을 사용하여 예측 결과를 비교하였으며, 파라미터는 아래의 표1과 같이 설정하였다. MAX_LEN은 token들의 max length인 142로 설정하였다.

![image](https://user-images.githubusercontent.com/79245351/159128262-82056638-277f-4825-b606-4d9042c9d11b.png)

**3.	 모델 성능 평가 결과**

![image](https://user-images.githubusercontent.com/79245351/159128273-2f5cfbe9-debe-4d16-bdce-6f12fab5219a.png)

BERT-multilingual 모델로 학습한 결과 87.2%의 성능을 보였으며, KoBERT의 경우 89.8%로 BERT-multilingual 모델 대비 2.6% 높은 성능을 보였다 (표2). 아무래도 KoBERT 모델의 경우 BERT-multilingual 모델에 한국어 위키 5백만 문장과 한국어 뉴스 2천만 문장을 추가로 학습하였기 때문에 한국어의 특성을 더 잘 파악하여 더 높은 성능을 보이는 것으로 보인다.
학습한 모델들이 새로운 리뷰도 잘 분류하는지 확인하기 위해 가장 최근 개봉한 영화인 <기적>과 <보이스>에 실제 작성된 리뷰 20개(긍정적 리뷰 10개, 부정적 리뷰 10개)로 테스트 해본 결과, 두 모델 모두 긍정/부정적 리뷰를 정확하게 분류하는 것을 확인하였다 (표3).

![image](https://user-images.githubusercontent.com/79245351/159128282-85e1a49f-023c-401b-9506-37c6ed57d2e4.png)
![image](https://user-images.githubusercontent.com/79245351/159128317-45ad7880-7058-4196-8415-31daa6e29aec.png)
