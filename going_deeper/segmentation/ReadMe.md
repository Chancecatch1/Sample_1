# AIFFEL Campus Online Code Peer Review Templete
- Coder : MyungJun Lee
- Reviewer : Taemin Kim


# PRT(Peer Review Template)


- [x]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**

  
> 루브릭
 1. U-Net을 통한 세그멘테이션 작업이 정상적으로 진행되었는가?<br/>
    - [ ] KITTI 데이터셋 구성, U-Net 모델 훈련, 결과물 시각화의 한 사이클이 정상 수행되어 세그멘테이션 결과 이미지를 제출하였다.
        - U-Net 모델은 시간 부족으로 모델 구성, 훈련을 진행하지 못했습니다.
 2. U-Net++ 모델이 성공적으로 구현되었는가?
    - [x] U-Net++ 모델을 스스로 구현하여 학습 진행 후 세그멘테이션 결과까지 정상 진행되었다.
        - ![image](https://github.com/Chancecatch1/aiffel_quest_mj/assets/29370771/6e2f1607-647d-4d24-b393-c20c38acadc0)

 3. U-Net과 U-Net++ 두 모델의 성능이 정량적/정성적으로 잘 비교되었는가?
    - [ ] U-Net++의 세그멘테이션 결과 사진과 IoU 계산치를 U-Net과 비교하여 우월함을 확인하였다.
        - U-Net 모델을 만들지 못하여 U-Net++ 모델과 비교하는 과정이 없습니다.
<br/><br/>
                 
- [x]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**
  - 모델 레이어 생성에서 부분마다 주석을 달아 무슨 레이어인지 알려주었습니다.
  - ![image](https://github.com/Chancecatch1/aiffel_quest_mj/assets/29370771/c9018238-0d9d-4281-960f-443a07a999ee)

<br/><br/>
      
- [x] **3. 에러가 난 부분을 디버깅하여 문제를 “해결한 기록을 남겼거나”, "새로운 시도 또는 추가 실험을 수행”해봤나요?**
  - deep_supervision을 사용하여 output들을 최종 결과로 사용하는 방법을 보였습니다.
  - ![image](https://github.com/Chancecatch1/aiffel_quest_mj/assets/29370771/e53e2d1c-45b9-47df-b627-5f66d93d4ef9)



- [x] **4. 회고를 잘 작성했나요?**
  - 아쉬운부분이 많은 프로젝트인것같습니다.
  - 시간만 많았다면 프로젝트를 잘 만드실꺼같습니다. 잘 작성했습니다.
  - ![image](https://github.com/Chancecatch1/aiffel_quest_mj/assets/29370771/b425439d-e045-4511-80da-d760331f518d)



- [x] **5. 코드가 간결하고 효율적인가요?**
  - 모든 부분에서 결과를 보기위해 코드가 간결하고 효율적입니다.

  
# 참고 링크 및 코드 개선
```
# 코드 리뷰 시 참고한 링크가 있다면 링크와 간략한 설명을 첨부합니다.
# 코드 리뷰를 통해 개선한 코드가 있다면 코드와 간략한 설명을 첨부합니다.
```

