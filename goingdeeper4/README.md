# AIFFEL Campus Online 5th Code Peer Review Templete
- 코더 :  조대호
- 리뷰어 : 본인의 이름을 작성하세요.


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [X] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
  
- [X] 주석을 보고 작성자의 코드가 이해되었나요?
  > 아래와 같이 주석을 자세히 작성해주셔서 쉽게 이해할 수 있었습니다.
  ```
  #크기 조정 및 정규화
  input_image, ratio = prepare_image(image)
  #사전에 정의한 추론 모델을 사용하여 입력 이미지로부터 검출 정보를 예측
  detections = inference_model.predict(input_image)
  #예측된 검출의 유효한 개수를 가져온다
  num_detections = detections.valid_detections[0]
  #예측된 검출의 클래스 인덱스를 클래스 이름으로 변환하여 리스트로 가져온다.
  class_names = [
    int2str(int(x)) for x in detections.nmsed_classes[0][:num_detections]
  ]
  #이미지와 검출 정보를 시각화하고 클래스별 높이와 너비 정보를 반환
  returned_ax, height_v, width_v, class_name = visualize_detections(
    image,
    detections.nmsed_boxes[0][:num_detections] / ratio,
    class_names,
    detections.nmsed_scores[0][:num_detections],
  )
  ```
- [X] 코드가 에러를 유발할 가능성이 없나요?
  > 결과가 바로바로 나와 에러가 없는 것을 볼 수 있습니다.
- [X] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  > 네 주석을 작성하신 걸 보면 잘이해하신것 같습니다.
- [X] 코드가 간결한가요?
  > 네 실행 결과가 바로 나와 간결하게 정리되어 있습니다.

# 예시
1. 코드의 작동 방식을 주석으로 기록합니다.
2. 코드의 작동 방식에 대한 개선 방법을 주석으로 기록합니다.
3. 참고한 링크 및 ChatGPT 프롬프트 명령어가 있다면 주석으로 남겨주세요.
```python
# 사칙 연산 계산기
class calculator:
    # 예) init의 역할과 각 매서드의 의미를 서술
    def __init__(self, first, second):
        self.first = first
        self.second = second
    
    # 예) 덧셈과 연산 작동 방식에 대한 서술
    def add(self):
        result = self.first + self.second
        return result

a = float(input('첫번째 값을 입력하세요.')) 
b = float(input('두번째 값을 입력하세요.')) 
c = calculator(a, b)
print('덧셈', c.add()) 
```

# 참고 링크 및 코드 개선
```python
# 코드 리뷰 시 참고한 링크가 있다면 링크와 간략한 설명을 첨부합니다.
# 코드 리뷰를 통해 개선한 코드가 있다면 코드와 간략한 설명을 첨부합니다.
```
