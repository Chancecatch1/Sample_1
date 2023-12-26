# AIFFEL Campus Online Code Peer Review Templete
- Coder : MyungJun Lee
- Reviewer : Taemin Kim


## 루브릭


1. multiface detection을 위한 widerface 데이터셋의 전처리가 적절히 진행되었다.
> tfrecord 생성, augmentation, prior box 생성 등의 과정이 정상적으로 진행되었다.
2. SSD 모델이 안정적으로 학습되어 multiface detection이 가능해졌다.
> inference를 통해 정확한 위치의 face bounding box를 detect한 결과이미지가 제출되었다.
3. 이미지 속 다수의 얼굴에 스티커가 적용되었다.
> 이미지 속 다수의 얼굴의 적절한 위치에 스티커가 적용된 결과이미지가 제출되었다.


# PRT(Peer Review Template)


- [x]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**
      
루브릭 1번 - 잘 수행 했습니다.
  1. tfrecord<br/>
    ![image](https://github.com/Chancecatch1/aiffel_quest_mj/assets/29370771/58abc304-1900-4fc7-84e3-b02d2d6efe13)
  
  2. augmentation<br/>
    ![image](https://github.com/Chancecatch1/aiffel_quest_mj/assets/29370771/9f78be97-5414-41f3-a9af-3ebec43a88f9)

  3. prior box<br/>
    ![image](https://github.com/Chancecatch1/aiffel_quest_mj/assets/29370771/6894b172-6483-446b-a58a-cf92bb084e26)


  루브릭 2번 - face가 아닌 부분도 잡지만 잡은 부분의 점수는 좋습니다.<br/>
  ![image](https://github.com/Chancecatch1/aiffel_quest_mj/assets/29370771/872a3057-592f-4817-97d0-2de4baa0863b)


  루브릭 3번 - 고양이 수염이 얼굴이 아닌 부분에 들어가긴 했지만 얼굴로 인식한 부분에는 잘 들어갔습니다.<br/>
  ![image](https://github.com/Chancecatch1/aiffel_quest_mj/assets/29370771/95e9a263-933c-4af9-aa8c-4c9f3caeabcc)


   

                 
- [x]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**

      핵심 적인 기술에 대한 부분에는 주석이 없지만, 랜드마크 만드는 부분에는 주석이 잘 작성돼어있습니다.
  ![image](https://github.com/Chancecatch1/aiffel_quest_mj/assets/29370771/3c7c35a4-322d-4180-bd9e-b037bfcc832f)




      
- [x] **3. 에러가 난 부분을 디버깅하여 문제를 “해결한 기록을 남겼거나”, "새로운 시도 또는 추가 실험을 수행”해봤나요?**

      epoch 마다 가중치를 저장했습니다.
  ![image](https://github.com/Chancecatch1/aiffel_quest_mj/assets/29370771/9cad5fbe-db80-41e0-92a7-9e17a875231b)



- [x] **4. 회고를 잘 작성했나요?**

      잘 작성했습니다.
  ![image](https://github.com/Chancecatch1/aiffel_quest_mj/assets/29370771/a25f5e41-10b7-4bbb-ad70-b3567632b512)



- [x] **5. 코드가 간결하고 효율적인가요?**
      
      랜드마크를 만드는 함수를 잘 작성했습니다.
  ![image](https://github.com/Chancecatch1/aiffel_quest_mj/assets/29370771/68166f6a-0416-4e5a-95b4-32ac29a72030)

  
# 참고 링크 및 코드 개선
```
# 코드 리뷰 시 참고한 링크가 있다면 링크와 간략한 설명을 첨부합니다.
# 코드 리뷰를 통해 개선한 코드가 있다면 코드와 간략한 설명을 첨부합니다.
```
