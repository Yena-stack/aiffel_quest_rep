# AIFFEL Campus Online Code Peer Review Templete
- 코더 : 조대호
- 리뷰어 : 조준규


# PRT(Peer Review Template)
- [X]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**
    - 루브릭에서 요구하는 사항을 모두 충족하였다.
```python
# 데이터셋 및 모델 준비
train_set = MJDatasetSequence(TRAIN_DATA_PATH, label_converter, batch_size=BATCH_SIZE, character=TARGET_CHARACTERS, is_train=True)
val_set = MJDatasetSequence(VALID_DATA_PATH, label_converter, batch_size=BATCH_SIZE, character=TARGET_CHARACTERS)
model = build_crnn_model()
```
```python
# End-to-End 함수 생성
ocr(HOME_DIR + '/sample3.jpg')
```  
    
- [X]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 
  주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**
    - 헷갈릴 수 있는 부분을 주석을 통해 어려워하지 않도록 하였다.
```python
checkpoint_path = HOME_DIR + '/crnn_weights.hdf5'
checkpoint = ModelCheckpoint(checkpoint_path, 
                             monitor="val_loss",  # 모니터링할 지표 (검증 손실)
                             save_best_only=True,  # 가장 좋은 결과만 저장
                             save_weights_only=True,  # 가중치만 저장
                             mode="min")  # 모니터링 지표가 최소화되어야 함

early_stopping = EarlyStopping(monitor="val_loss",  # 모니터링할 지표 (검증 손실)
                               patience=3,  # 훈련이 중지되기 전에 지정된 횟수의 에포크를 기다립니다
                               restore_best_weights=True)  # 최상의 가중치로 복원

```
  
- [X]  **3. 에러가 난 부분을 디버깅하여 문제를 “해결한 기록을 남겼거나” 
  ”새로운 시도 또는 추가 실험을 수행”해봤나요?**
    - 이미지를 랜덤으로 회전하여도 잘 인식하는지 확인해보는 추가 실험을 수행하였다.
```python
rotated_image = PIL.Image.open(SAMPLE_IMG_PATH).rotate(-30)
sample_lotate_path = HOME_DIR + '/sample_lotate_30.jpg'
rotated_image.save(sample_lotate_path)

ocr(sample_lotate_path)
```
  
- [X]  **4. 회고를 잘 작성했나요?**
    - 각 이미지 테스트 별로 장단점을 찾고 추가로 성능을 향상시킬 수 있는 방법을 찾고자 하였다.
```
Recognition 모델의 학습이 충분하지 못한 부분이 있어 노드에서 제공된 학습된 모델의 가중치로 테스트해 본 결과 비슷한 성능을 확인하였다. 따라서 OCR이 어려워지는 이유는 이미지의 불규칙한 방향이나 휘어진 진행 방향 때문인 것으로 보인다.

16번 학습 노드에서 소개된 논문 Robust Scene Text Recognition With Automatic Rectification에서는 Thin Plate Spline (TPS) Transformation을 적용하여 입력 이미지를 단어 영역에 맞게 변형 시켜 인식이 잘되도록 해준다면 인식 성능을 높일 수 있을 것 같다.

추가적으로 Detector로 검출된 텍스트 이미지 영역을 수평하게 회전시켜 Recognition 모델로 추론하는 것으로도 인식 성능을 높일 수 있을 것 같다.
```
    
- [X]  **5. 코드가 간결하고 효율적인가요?**
    - 코드를 최소화하기 위해 함수를 적절히 사용하였다.
```python
def ocr(image_path):    
    img_pil, cropped_imgs = detect_text(image_path)
    display(img_pil)
    for img in cropped_imgs:
        recognize_img(img)

ocr(SAMPLE_IMG_PATH)
```


# 참고 링크 및 코드 개선
```
# 코드 리뷰 시 참고한 링크가 있다면 링크와 간략한 설명을 첨부합니다.
# 코드 리뷰를 통해 개선한 코드가 있다면 코드와 간략한 설명을 첨부합니다.
```
