# AIFFEL Campus Online Code Peer Review Templete
- 코더 : 이명준
- 리뷰어 : 김민규


# PRT(Peer Review Template)

---

- [x]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**


| 평가문항                                                                    | 상세기준        | 달성여부 |
| --------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- | -------- |
| 1. ResNet-34, ResNet-50 모델 구현이 정상적으로 진행되었는가?                | 블록함수 구현이 제대로 진행되었으며 구현한 모델의 summary가 예상된 형태로 출력되었다                     | o        |
| 2. 구현한 ResNet 모델을 활용하여 Image Classification 모델 훈련이 가능한가? | tensorflow-datasets에서 제공하는 cats_vs_dogs 데이터셋으로 학습 진행 시 loss가 감소하는 것이 확인되었다. | o        |
| 3. Ablation Study 결과가 바른 포맷으로 제출되었는가?      | ResNet-34, ResNet-50 각각 plain모델과 residual모델을 동일한 epoch만큼 학습시켰을 때의 validation accuracy 기준으로 Ablation Study 결과표가 작성되었다.                                                           |   0   |



---
    
- [x]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 
주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**

- 모델 빌드하는 부분
![image](https://github.com/Chancecatch1/aiffel_quest_mj/assets/68997408/03d69dff-6f9e-4ece-b5a0-2b39390c74bf)




---
        
- [x]  **3. 에러가 난 부분을 디버깅하여 문제를 “해결한 기록을 남겼거나” 
”새로운 시도 또는 추가 실험을 수행”해봤나요?**

-  resnet34 vs depth 34 without skip connection  
  
![image](https://github.com/Chancecatch1/aiffel_quest_mj/assets/68997408/cbf5888c-d8fa-45af-a306-d3026587518f)
![image](https://github.com/Chancecatch1/aiffel_quest_mj/assets/68997408/acfdbd0c-ec1f-4614-a190-fa4bc6e17f4f)



---
        
- [ ]  **4. 회고를 잘 작성했나요?**


---


        
- [x]  **5. 코드가 간결하고 효율적인가요?**

- residual block 부분, for문으로 간결하게 작성

![image](https://github.com/Chancecatch1/aiffel_quest_mj/assets/68997408/939bd014-12d7-4515-94da-6d7aa4057877)



# 참고 링크 및 코드 개선

- 삼항 연산자로 모델을 깔끔하게 작성할 수 있습니다.
```python
shortcut = tf.keras.layers.Conv2D(filters_1, 1, 
                                  strides=2 if i==0 else 1, 
                                  activation=None, 
                                  padding='same')(x)

```

