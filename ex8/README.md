# AIFFEL Campus Online Code Peer Review Templete
- Coder : MyungJun Lee
- Reviewer : Minsung Seo


## 루브릭

1. 한국어 전처리를 통해 학습 데이터셋을 구축하였다.
> 공백과 특수문자 처리, 토크나이징, 병렬데이터 구축의 과정이 적절히 진행되었다.
3. 트랜스포머 모델을 구현하여 한국어 챗봇 모델 학습을 정상적으로 진행하였다.
> 구현한 트랜스포머 모델이 한국어 병렬 데이터 학습 시 안정적으로 수렴하였다.
3. 한국어 입력문장에 대해 한국어로 답변하는 함수를 구현하였다.
> 한국어 입력문장에 맥락에 맞는 한국어로 답변을 리턴하였다.


# PRT(Peer Review Template)


- [ ]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**

  
> 문제에서 요구하는 최종 결과물이 첨부되었는지 확인
> 문제를 해결하는 완성된 코드란 프로젝트 루브릭 3개 중 2개, 퀘스트 문제 요구조건 등을 지칭
> 해당 조건을 만족하는 코드를 캡쳐해 근거로 첨부
  - 한국어 전처리를 통해 학습 데이터셋을 구축하였다.
    - 공백과 특수문자 처리, 토크나이징, 병렬데이터 구축의 과정이 적절히 진행되었다.
    - ![스크린샷 2023-10-12 오후 12 27 48](https://github.com/Chancecatch1/aiffel_quest_mj/assets/138687269/60c9364a-0bc9-4c52-b6ca-18ef445a028c)

  - 트랜스포머 모델을 구현하여 한국어 챗봇 모델 학습을 정상적으로 진행하였다.
    - 구현한 트랜스포머 모델이 한국어 병렬 데이터 학습 시 안정적으로 수렴하였다.
    - ![스크린샷 2023-10-12 오후 12 29 49](https://github.com/Chancecatch1/aiffel_quest_mj/assets/138687269/87d19dba-28ce-4f4a-af47-9e391e0a57d6)
  - 한국어 입력문장에 대해 한국어로 답변하는 함수를 구현하였다.
    - 한국어 입력문장에 맥락에 맞는 한국어로 답변을 리턴하였다.
    - 네 구현 및 리턴되었습니다.
    - ![스크린샷 2023-10-12 오후 12 31 00](https://github.com/Chancecatch1/aiffel_quest_mj/assets/138687269/ee94230e-99e5-41e5-9208-4b763af4e959)
    - ![스크린샷 2023-10-12 오후 12 31 41](https://github.com/Chancecatch1/aiffel_quest_mj/assets/138687269/e08ba4c2-95af-493a-ade5-d2497f6db1c1)
                 
- [ ]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**


> 해당 코드 블럭에 doc string/annotation이 달려 있는지 확인
  > 네 달려있습니다. 
> 해당 코드가 무슨 기능을 하는지, 왜 그렇게 짜여진건지, 작동 메커니즘이 뭔지 기술.
> 챗봇을 테스트하기 위한 함수로서 예측한 단어가 토큰이라면 종료하여 예측된 단어들의 집합을 문장으로 반환하는 함수입니다.
```
def decoder_inference(sentence):
    sentence = preprocess_sentence(sentence)

    # 입력된 문장을 정수 인코딩 후, 시작 토큰과 종료 토큰을 앞뒤로 추가.
    sentence = tf.expand_dims(
        START_TOKEN + tokenizer.encode(sentence) + END_TOKEN, axis=0)
    
    # 디코더의 현재까지의 예측한 출력 시퀀스가 지속적으로 저장되는 변수.
    # 처음에는 예측한 내용이 없음으로 시작 토큰만 별도 저장. ex) 8331
    output_sequence = tf.expand_dims(START_TOKEN, 0)
    
    # 디코더의 인퍼런스 단계
    for i in range(MAX_LENGTH):
        # 디코더는 최대 MAX_LENGTH의 길이만큼 다음 단어 예측을 반복합니다.
        predictions = model(inputs=[sentence, output_sequence], training=False)
        predictions = predictions[:, -1:, :]

        # 현재 예측한 단어의 정수
        predicted_id = tf.cast(tf.argmax(predictions, axis=-1), tf.int32)

        # 만약 현재 예측한 단어가 종료 토큰이라면 for문을 종료
        if tf.equal(predicted_id, END_TOKEN[0]):
            break
        # 예측한 단어들은 지속적으로 output_sequence에 추가됩니다.
        # 이 output_sequence는 다시 디코더의 입력이 됩니다.
        output_sequence = tf.concat([output_sequence, predicted_id], axis=-1)

    return tf.squeeze(output_sequence, axis=0)
```
> 주석을 보고 코드 이해가 잘 되었는지 확인
> 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.

      
- [ ] **3. 에러가 난 부분을 디버깅하여 문제를 “해결한 기록을 남겼거나”, "새로운 시도 또는 추가 실험을 수행”해봤나요?**

        
> 문제 원인 및 해결 과정을 잘 기록하였는지 확인
  > 해당부분은 확인하기 어려웠습니다.
> 문제에서 요구하는 조건에 더해 추가적으로 수행한 나만의 시도, 실험이 기록되어 있는지 확인
  > 해당부분은 확인하기 어려웠습니다. 
> 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.
> ![스크린샷 2023-10-12 오후 12 49 19](https://github.com/Chancecatch1/aiffel_quest_mj/assets/138687269/c7457dc4-bbe1-4985-91de-616a44d0d0e4)



- [ ] **4. 회고를 잘 작성했나요?**


> 주어진 문제를 해결하는 완성된 코드 내지 프로젝트 결과물에 대해 배운점과 아쉬운점, 느낀점 등이 기록되어 있는지 확인
  > 회고는 작성되어있지 않아 아쉬웠습니다.
> 전체 코드 실행 플로우를 그래프로 그려서 이해를 돕고 있는지 확인
> 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.


- [ ] **5. 코드가 간결하고 효율적인가요?**

 
> 파이썬 스타일 가이드 (PEP8) 를 준수하였는지 확인
> 하드코딩을 하지않고 함수화, 모듈화가 가능한 부분은 함수를 만들거나 클래스로 짰는지
  > 모델 학습 및 출력을 함수를 선언하여 진행하였습니다.
  > 다만 하기의 함수를 선언하게 되면 실험결과 확인시 매번 학습을 진행해야하는 문제가 발생됩니다. 
> 코드 중복을 최소화하고 범용적으로 사용할 수 있도록 함수화했는지
> 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.
  > ![스크린샷 2023-10-12 오후 12 47 04](https://github.com/Chancecatch1/aiffel_quest_mj/assets/138687269/bd1077fa-55a7-4a00-94bd-51b8ccecf63c)


  
# 참고 링크 및 코드 개선
```
# 코드 리뷰 시 참고한 링크가 있다면 링크와 간략한 설명을 첨부합니다.
# 코드 리뷰를 통해 개선한 코드가 있다면 코드와 간략한 설명을 첨부합니다.
```
