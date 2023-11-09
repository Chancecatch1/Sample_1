
# AIFFEL Campus Online Code Peer Review Templete
- Coder : MyungJun Lee
- Reviewer : San Kim


## 루브릭


1. CutMix와 MixUp 기법을 ResNet50 분류기에 성공적으로 적용하였는가?
  > CutMix와 MixUp을 적용한 데이터셋으로 훈련한 각각의 ResNet 모델이 수렴하였다.
2. 다양한 실험을 통해 태스크에 최적인 Augmentation 기법을 찾아내었는가?
  > 각 Augmentation 기법을 적용하고, 그에 따른 성능 비교 분석 및 문제점을 서술하였음
3. 여러가지 Augmentation 기법을 적용한 결과를 체계적으로 비교분석하였는가?
  > 기본 Augmentation, CutMix, MixUp이 적용된 결과를 시각화와 함께 체계적으로 분석하였다.


# PRT(Peer Review Template)


- [x]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**

  
> cutmix / mixup 기법을 적용했을 뿐만 아니라 이를 조합하여 더 많은 경우에 대해서도 모델 성능에 대한 실험을 적용하였다.

<img width="523" alt="스크린샷 2023-11-09 오후 5 40 59" src="https://github.com/3n952/aiffel_quest_mj/assets/107621083/75d0be5d-5303-4017-84a0-e1b9a22eebca">
<img width="523" alt="스크린샷 2023-11-09 오후 5 40 40" src="https://github.com/3n952/aiffel_quest_mj/assets/107621083/2e4c52f3-a170-446b-be7e-1bf83c05cfe0">
<img width="523" alt="스크린샷 2023-11-09 오후 5 41 08" src="https://github.com/3n952/aiffel_quest_mj/assets/107621083/e251e563-ade1-4c67-b082-3da5d0538705">

                 
- [x]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**


> 해당 코드 블럭에 doc string을 적절하게 사용하여 어떠한 실험을 하고자 했는지 파악 할 수 있었다.
> 하지만 코드에 대한 annotation이 조금 부족하다고 느껴졌다.
<img width="822" alt="스크린샷 2023-11-09 오후 5 43 22" src="https://github.com/3n952/aiffel_quest_mj/assets/107621083/c4e9ebb3-b920-489b-8c20-3c566db4e9cc">
<img width="698" alt="스크린샷 2023-11-09 오후 5 43 07" src="https://github.com/3n952/aiffel_quest_mj/assets/107621083/d48da1fd-a40b-43a8-b9cf-66d3ad5dcd41">


      
- [x] **3. 에러가 난 부분을 디버깅하여 문제를 “해결한 기록을 남겼거나”, "새로운 시도 또는 추가 실험을 수행”해봤나요?**

        
> augmetation에서 발생된 성능 문제 원인 및 해결 과정을 잘 기록하였다.
> 문제에서 요구하는 조건에 더해 추가적으로 수행한 나만의 시도, 실험이 기록되어 있지만 결과에 대한 기록은 없는 것 같다.
<img width="917" alt="스크린샷 2023-11-09 오후 5 46 21" src="https://github.com/3n952/aiffel_quest_mj/assets/107621083/dd41d8ad-add8-4fb6-a88b-c5adb4ab5a76">
<img width="917" alt="스크린샷 2023-11-09 오후 5 47 11" src="https://github.com/3n952/aiffel_quest_mj/assets/107621083/811a7daf-4e22-4a43-b7bf-84f7525fbd48">



- [] **4. 회고를 잘 작성했나요?**

> 주어진 문제를 해결하는 완성된 코드 내지 프로젝트 결과물에 대해 배운점과 아쉬운점, 느낀점 등이 기록되어 있는 부분은 따로 없는 것 같다. 



- [x] **5. 코드가 간결하고 효율적인가요?**

 
> 파이썬 스타일 가이드 (PEP8) 를 준수하고, 함수화, 모듈화가 가능한 부분은 함수를 만들거나 클래스로 짰다.
<img width="909" alt="스크린샷 2023-11-09 오후 5 48 30" src="https://github.com/3n952/aiffel_quest_mj/assets/107621083/5d078b6e-df13-4499-a79f-25b93ab74504">
<img width="909" alt="스크린샷 2023-11-09 오후 5 48 43" src="https://github.com/3n952/aiffel_quest_mj/assets/107621083/46fffa3d-f753-4a64-b414-82643b4b4349">


