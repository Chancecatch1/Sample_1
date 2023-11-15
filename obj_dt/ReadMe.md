
# AIFFEL Campus Online Code Peer Review Templete
- 코더 : 이명준
- 리뷰어 : 이동희


# PRT(Peer Review Template)
- [x]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**
    - 문제에서 요구하는 최종 결과물이 첨부되었는지 확인
    - 문제를 해결하는 완성된 코드란 프로젝트 루브릭 3개 중 2개, 
    퀘스트 문제 요구조건 등을 지칭
> 1. KITTI 데이터셋에 대한 분석이 체계적으로 진행되었다. -> O
> 2. RetinaNet 학습이 정상적으로 진행되어 object detection 결과의 시각화까지 진행되었다. -> O
> 3. 율주행 Object Detection 테스트시스템 적용결과 만족스러운 정확도 성능을 달성하였다. -> X
    
- [ ]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 
주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**
    - 해당 코드 블럭에 doc string/annotation이 달려 있는지 확인
    - 해당 코드가 무슨 기능을 하는지, 왜 그렇게 짜여진건지, 작동 메커니즘이 뭔지 기술.
    - 주석을 보고 코드 이해가 잘 되었는지 확인
> 주석이 하나도 없습니다..
        
- [ ]  **3. 에러가 난 부분을 디버깅하여 문제를 “해결한 기록을 남겼거나” 
”새로운 시도 또는 추가 실험을 수행”해봤나요?**
    - 문제 원인 및 해결 과정을 잘 기록하였는지 확인
    - 문제에서 요구하는 조건에 더해 추가적으로 수행한 나만의 시도, 
    실험이 기록되어 있는지 확인

        
- [x]  **4. 회고를 잘 작성했나요?**
    - 주어진 문제를 해결하는 완성된 코드 내지 프로젝트 결과물에 대해
    배운점과 아쉬운점, 느낀점 등이 기록되어 있는지 확인
    - 전체 코드 실행 플로우를 그래프로 그려서 이해를 돕고 있는지 확인
> 시간이 없어서 아쉬웠지만. Yolo모델의 원리를 조금이나마 알게되어서 보람있었다. 70점이 나온 부분은 시간이 있을 때 조금 더 연구해보고 싶었다.
        
- [x]  **5. 코드가 간결하고 효율적인가요?**
    - 파이썬 스타일 가이드 (PEP8) 를 준수하였는지 확인
    - 하드코딩을 하지않고 함수화, 모듈화가 가능한 부분은 함수를 만들거나 클래스로 짰는지
    - 코드 중복을 최소화하고 범용적으로 사용할 수 있도록 함수화했는지
```python
def self_drive_assist(img_path, size_limit=300):
    image = Image.open(img_path)
    image = np.array(image, dtype=np.uint8)

    image = tf.cast(image, dtype=tf.float32)
    
    input_image, ratio = prepare_image(image)
    detections = inference_model.predict(input_image)
    num_detections = detections.valid_detections[0]
    
    
    class_names = [
        int2str(int(x)) for x in detections.nmsed_classes[0][:num_detections]
    ] 
    
    visualize_detections(
        image,
        detections.nmsed_boxes[0][:num_detections] / ratio,
        class_names,
        detections.nmsed_scores[0][:num_detections],
    )
    
    boxes = detections.nmsed_boxes[0][:num_detections] / ratio
    
    for class_name, detected_box in zip(class_names, boxes):
        x1, y1, x2, y2 = detected_box
        
        width = (x2-x1)/ratio
        height = (y2-y1)/ratio
        
        if class_name == 'Pedestrian':
            return 'Stop'

        if class_name == 'Car':
            if width >= size_limit or height >= size_limit:
                return 'Stop'
            else:
                return 'Go'
    return "Go"
```


# 참고 링크 및 코드 개선
```
# 코드 리뷰 시 참고한 링크가 있다면 링크와 간략한 설명을 첨부합니다.
# 코드 리뷰를 통해 개선한 코드가 있다면 코드와 간략한 설명을 첨부합니다.
```
