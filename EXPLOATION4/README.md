# AIFFEL Campus Online 5th Code Peer Review 
- 코더 : 조대호
- 리뷰어 : 황인준


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [X] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
목표하던 85%의 정확도에 도달하지는 못했다
- [O] 주석을 보고 작성자의 코드가 이해되었나요?
```python
from konlpy.tag import Okt # Mecab이 colab상에서 실행되지 않아 okt를 사용
```
- [X] 코드가 에러를 유발할 가능성이 없나요?
  CNN 모델을 선언할때 word vector의 크기가 커진 경우 에러가 발생해서 word vector의 크기를 4로 잡았다.
  만일 성능을 높이기 위해 word vector의 크기를 키우면 에러가 발생할 가능성이 있다.
```python
vocab_size = 10000  # 어휘 사전의 크기
word_vector_dim = 4  # 단어 하나를 표현하는 임베딩 벡터의 차원 수

model_2 = tf.keras.Sequential()
model_2.add(tf.keras.layers.Embedding(vocab_size, word_vector_dim, input_shape=(None,)))
model_2.add(tf.keras.layers.Conv1D(16, 7, activation='relu', padding ='same'))
#Conv1D에 padding='same'한 이유는
#벡터의 차원의 수가 적어서 차원이 마이너스로 가벼러서 padding='same'을 주어
#출력길이와 입력길이를 동일하게 했습니다.
model_2.add(tf.keras.layers.MaxPooling1D(5))
model_2.add(tf.keras.layers.Conv1D(16, 7, activation='relu', padding ='same'))
model_2.add(tf.keras.layers.GlobalMaxPooling1D())
model_2.add(tf.keras.layers.Dense(8, activation='relu'))
model_2.add(tf.keras.layers.Dense(1, activation='sigmoid'))  # 최종 출력은 긍정/부정을 나타내는 1dim 입니다.

model_2.summary()
```
- [O] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  > 주석도 잘 했고, 결과를 내기 위한 여러 흔적들이 보인다
- [Δ] 코드가 간결한가요?
  > 비슷한 연산에 대해서 함수화도 가능했을 수도 있다.
```python
  train_data.drop_duplicates(subset=['document'], inplace=True)
  train_data = train_data.dropna(how = 'any')
  test_data.drop_duplicates(subset=['document'], inplace=True)
  test_data = test_data.dropna(how = 'any')
  X_train = []
  for sentence in train_data['document']:
    temp_X = tokenizer.morphs(sentence) # 토큰화
    temp_X = [word for word in temp_X if not word in stopwords] # 불용어 제거
    X_train.append(temp_X)
  X_test = []
  for sentence in test_data['document']:
    temp_X = tokenizer.morphs(sentence) # 토큰화
    temp_X = [word for word in temp_X if not word in stopwords] # 불용어 제거
    X_test.append(temp_X)
```


# 참고 링크 및 코드 개선
```python
# data pre-pre-process part

def process_data(data):
    data.drop_duplicates(subset=['document'], inplace=True)  # 데이터 중복 제거
    data = data.dropna(how = 'any')  # NaN 결측치 제거
    processed_data = []   
    for comment in data['document']:      # for each comments,
        tokenized_comment = tokenizer.morphs(comment)  # 한국어 토크나이저로 토큰화
        tokenized_comment = [token for token in tokenized_comment if not token in stopwords]  # 불용어(Stopwords) 제거
        processed_data.append(tokenized_comment)   # gather processed data
    return processed_data, np.array(list(data['label']))     # return words & target
```
