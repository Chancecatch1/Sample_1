
# AIFFEL Campus Online Code Peer Review Templete
- Coder : MyungJun Lee
- Reviewer : Taemin Kim


## 루브릭


1. tfrecord를 활용한 데이터셋 구성과 전처리를 통해 프로젝트 베이스라인 구성을 확인하였다.
> MPII 데이터셋을 기반으로 1epoch에 30분 이내에 학습가능한 베이스라인을 구축하였다.
2. simplebaseline 모델을 정상적으로 구현하였다.
> simplebaseline 모델을 구현하여 실습코드의 모델을 대체하여 정상적으로 학습이 진행되었다.
3. Hourglass 모델과 simplebaseline 모델을 비교분석한 결과를 체계적으로 정리하였다.
> 두 모델의 pose estimation 테스트결과 이미지 및 학습진행상황 등을 체계적으로 비교분석하였다.


# PRT(Peer Review Template)


- [x]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**

  
루브릭
- [x] 1. MPII 데이터셋을 기반으로 1epoch에 30분 이내에 학습가능한 베이스라인을 구축하였다.
      
      - 1epoch당 몇분이 걸렸는지는 모르겠지만 대략 20~25분 걸린것으로 보인다.
      
- [x] 2. simplebaseline 모델을 구현하여 실습코드의 모델을 대체하여 정상적으로 학습이 진행되었다.

      - 분산전략으로는 학습이 안돼서 분산전략을 simplebaseline모델에서는 제거하여 학습했다.
      
- [x] 3. 두 모델의 pose estimation 테스트 결과 이미지 및 학습진행상황 등을 체계적으로 비교분석하였다.

      - 두 모델의 pose estimation 결과를 비교분석하였습니다.
![image](https://github.com/Chancecatch1/aiffel_quest_mj/assets/29370771/bde21468-c4b6-421e-82c4-7eed795c1143)


                 
- [x]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**

      - 분산학습하면 simplebaseline 모델에서는 오류가 발생하는데 이를 분산전략을 없애고 학습하는 방식으로 잘 작성했습니다.
![image](https://github.com/Chancecatch1/aiffel_quest_mj/assets/29370771/3ef8a07e-60d2-40f4-a64b-be5678cc37f2)

      
- [x] **3. 에러가 난 부분을 디버깅하여 문제를 “해결한 기록을 남겼거나”, "새로운 시도 또는 추가 실험을 수행”해봤나요?**

      - input shape와 output shape를 확인하기 위해서 확인한 결과를 볼 수 있다.
![image](https://github.com/Chancecatch1/aiffel_quest_mj/assets/29370771/461d5b66-68e3-4648-a24f-eddc7b04572b)

![image](https://github.com/Chancecatch1/aiffel_quest_mj/assets/29370771/bcb2483a-6307-4044-be90-6064f26f6f27)




- [x] **4. 회고를 잘 작성했나요?**

      잘 작성했습니다.
![image](https://github.com/Chancecatch1/aiffel_quest_mj/assets/29370771/f97cbae7-def8-489c-8cfb-0d89112c07eb)



- [x] **5. 코드가 간결하고 효율적인가요?**

      - 기존 StackedHourglass 모델의 train 함수를 simplebaseline 모델에 맞는 train 함수로 잘 변형하고 간결하고 효율적으로 작성했습니다.
![image](https://github.com/Chancecatch1/aiffel_quest_mj/assets/29370771/0b57b9ec-a546-4a46-b2b1-c669421a83db)


  
# 참고 링크 및 코드 개선
```
# 코드 리뷰 시 참고한 링크가 있다면 링크와 간략한 설명을 첨부합니다.
# 코드 리뷰를 통해 개선한 코드가 있다면 코드와 간략한 설명을 첨부합니다.
```
