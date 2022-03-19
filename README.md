# BERT-movie-review-sentiment-classification

1.	데이터셋
Naver sentiment movie corpus (rating_train.txt, rating_test.txt) 데이터 셋을 사용하였으며, rating_train.txt를 사용하여 모델 생성 후 rating_test.txt를 사용하여 예측 실행하였다. Train data는 15만개, Test data는 5만개의 리뷰로 이루어져 있다.

2.	사용 모델 및 하이퍼 파라미터
104개의 언어로 된 말뭉치로 사전 학습한 모델인 BERT-multilingual과 SKTBrain에서 개발한 한국어에 특화된 KoBERT 모델을 사용하여 예측 결과를 비교하였으며, 파라미터는 아래의 표1과 같이 설정하였다. MAX_LEN은 token들의 max length인 142로 설정하였다.
Parameters	모델1: BERT-multilingual	모델2: KoBERT
Batch Size	32	32
MAX_LEN	142	142
Learning rate	2e-5	5e-5
epochs	4	4
표 1 사용 모델 및 모델 학습에 사용한 파라미터

3.	 모델 성능 평가 결과
모델	정확도
BERT-multilingual	87.2%
KoBERT	89.8%
표 2 모델별 감성 분석 결과

BERT-multilingual 모델로 학습한 결과 87.2%의 성능을 보였으며, KoBERT의 경우 89.8%로 BERT-multilingual 모델 대비 2.6% 높은 성능을 보였다 (표2). 아무래도 KoBERT 모델의 경우 BERT-multilingual 모델에 한국어 위키 5백만 문장과 한국어 뉴스 2천만 문장을 추가로 학습하였기 때문에 한국어의 특성을 더 잘 파악하여 더 높은 성능을 보이는 것으로 보인다.
학습한 모델들이 새로운 리뷰도 잘 분류하는지 확인하기 위해 가장 최근 개봉한 영화인 <기적>과 <보이스>에 실제 작성된 리뷰 20개(긍정적 리뷰 10개, 부정적 리뷰 10개)로 테스트 해본 결과, 두 모델 모두 긍정/부정적 리뷰를 정확하게 분류하는 것을 확인하였다 (표3). 


No.	리뷰	BERT-multilingual	KoBERT
1	간만에 감동 준 영화ㅠㅠ	긍정	긍정
2	잔잔하고 마음 따뜻해지는 영화입니다. 배우들의 연기가 좋았어요.	긍정	긍정
3	훈훈한 영화에요 가족들이랑 같이 보러가서 여러번 눈물 흘렸습니다	긍정	긍정
4	잔잔하고 마음 따뜻해지는 영화입니다. 배우들의 연기가 좋았어요.	긍정	긍정
5	감동이에요.. 마음이 따뜻해지는 영화	긍정	긍정
6	배우님들 연기도 정말 다 최고구 영상미연출스토리 머하나 빠지는 게 없는 영화입니다. 형제자매가 있다면 더 공감갈만한 영화였어요 저는 정말 재미있게 봤네요	긍정	긍정
7	아주 눈물콧물 다뺌 휴지 안챙겨 가서 낭패봤어요	긍정	긍정
8	진짜 영화로 만들어줘서 너무 감동입니다!보는내내 시간 안본거 처음입니다이 영화보구 아무도 안당했으면 좋겠습니다!변요한 김무열 최고네요 !	긍정	긍정
9	재밌어요. 전개가 나름빠르고 연기도 좋습니다.	긍정	긍정
10	지루하지않고,사실적표현등 좋았음.경각심도 불러올수있었고 good~	긍정	긍정
11	출연한 모든 배우들의 흑역사	부정	부정
12	100억 갖다 버리는게 더 재밌겠다	부정	부정
표 3 새로운 리뷰 테스트 결과

