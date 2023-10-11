# AIFFEL Campus Online Code Peer Review Templete
- Coder : MyungJun Lee
- Reviewer : 김민규


## 루브릭


1. pix2pix 모델 학습을 위해 필요한 데이터셋을 적절히 구축하였다.
> 데이터 분석 과정 및 한 가지 이상의 augmentation을 포함한 데이터셋 구축 과정이 체계적으로 제시되었다.
2. pix2pix 모델을 구현하여 성공적으로 학습 과정을 진행하였다.
> U-Net generator, discriminator 모델 구현이 완료되어 train_step의 output을 확인하고 개선하였다.
3. 학습 과정 및 테스트에 대한 시각화 결과를 제출하였다.
> 10 epoch 이상의 학습을 진행한 후 최종 테스트 결과에서 진행한 epoch 수에 걸맞은 정도의 품질을 확인하였다.


# PRT(Peer Review Template)


- [x]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**
  - data generator 구축 (o)
    ![image](https://github.com/Chancecatch1/aiffel_quest_mj/assets/68997408/78f8406b-5268-4b89-ab11-4fd2f769d90c)
  - 학습 과정 진행 (o)
    ![image](https://github.com/Chancecatch1/aiffel_quest_mj/assets/68997408/827b81a1-5837-4215-bd5b-00b724df08da)
  - 시각화 (x)
                 
- [x]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**
  - 모델 빌드 부분
    ![image](https://github.com/Chancecatch1/aiffel_quest_mj/assets/68997408/f4c33f01-5f84-43fe-8a64-3c1a34599a5b)

      
- [ ] **3. 에러가 난 부분을 디버깅하여 문제를 “해결한 기록을 남겼거나”, "새로운 시도 또는 추가 실험을 수행”해봤나요?**



- [ ] **4. 회고를 잘 작성했나요?**


- [x] **5. 코드가 간결하고 효율적인가요?**
  - 테스트 시각화
    ![image](https://github.com/Chancecatch1/aiffel_quest_mj/assets/68997408/f59d6813-bb0c-4498-b317-ed3a63518b6c)

> 파이썬 스타일 가이드 (PEP8) 를 준수하였는지 확인
> 하드코딩을 하지않고 함수화, 모듈화가 가능한 부분은 함수를 만들거나 클래스로 짰는지
> 코드 중복을 최소화하고 범용적으로 사용할 수 있도록 함수화했는지
> 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.

  
# 참고 링크 및 코드 개선
> 모델 빌드하는 부분에서 아래 코드 참고하셔도 좋을 것 같습니다!
```python
for i, f in enumerate(filters):
            self.blocks.append(DiscBlock(n_filters=f,
                                         stride=2 if i < 3 else 1, 
                                         custom_pad=False if i < 3 else True, 
                                         use_bn=False if i < 5 else True, 
                                         act=True if i < 5 else False))
```
