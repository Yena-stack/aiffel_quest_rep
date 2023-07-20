# AIFFEL Campus Online 5th Code Peer Review Templete
- 코더 : 조대호
- 리뷰어 : 신유진


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [X] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
  > 넵, 정상작동힘.
- [X] 주석을 보고 작성자의 코드가 이해되었나요?
  > 넵, 각 단계별로, 그리고 코드 내에서도 주석처리가 잘 되어있어 알아보기 쉬움.
- [X] 코드가 에러를 유발할 가능성이 없나요?
  > 없음, 
- [X] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  > 넵, 모든 플로우를 정확하게 숙지하고 계신걸로 판단됨.
- [X] 코드가 간결한가요?
  > 넵, 데이터의 분포를 확인하는 코드가 함수로 자동화 되어있어서 간결하고 알아보기 쉬웠음.

# 예시
1. 코드의 작동 방식을 주석으로 기록합니다.
2. 코드의 작동 방식에 대한 개선 방법을 주석으로 기록합니다.
3. 참고한 링크 및 ChatGPT 프롬프트 명령어가 있다면 주석으로 남겨주세요.
```python
# 코드의 흐름 및 함수는 대략 다음과 같다. 
step1 데이터 불러오기

step2 데이터 전처리
def preprocess_sentence(sentence):
def load_conversations():

step3 SubwordTextEncoder
def visualize_sentence_lengths(sentences):
def tokenize_and_filter(inputs, outputs):

step4 모델구성
class PositionalEncoding(tf.keras.layers.Layer):
def scaled_dot_product_attention(query, key, value, mask):

class MultiHeadAttention(tf.keras.layers.Layer):
def create_padding_mask(x):
def create_look_ahead_mask(x):
def encoder_layer(units, d_model, num_heads, dropout, name="encoder_layer"):
def encoder(파라미터 많아서 생략):
def decoder_layer(units, d_model, num_heads, dropout, name="decoder_layer"):
def decoder(파라미터 많아서 생략):
def transformer(파라미터 많아서 생략):
model.summary()
def loss_function(y_true, y_pred):
class CustomSchedule(tf.keras.optimizers.schedules.LearningRateSchedule):
plt.show()
model.compile()
model.fit()

step5 모델 평가하기
def decoder_inference(sentence):
def sentence_generation(sentence):

```

# 참고 링크 및 코드 개선
```python
# 이것저것 검색하다가 발견한 사이트입니다. https://wikidocs.net/89786
# 코드의 진행방향과 회고까지 읽으면서 대호님이 생각하신 부분도 충분히 고려할 만한 상황이라고 생각됩니다. 그 결과가 저도 궁금해지네요.
# 고생하셨습니다 👍
```
