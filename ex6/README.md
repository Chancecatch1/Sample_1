# AIFFEL Campus Online Code Peer Review Templete
- Coder : MyungJun Lee
- Reviewer : 이동희


## 루브릭


1. Abstractive 모델 구성을 위한 텍스트 전처리 단계가 체계적으로 진행되었다.
> 분석단계, 정제단계, 정규화와 불용어 제거, 데이터셋 분리, 인코딩 과정이 빠짐없이 체계적으로 진행되었다.

2. 텍스트 요약모델이 성공적으로 학습되었음을 확인하였다.
> 모델 학습이 진행되면서 train loss와 validation loss가 감소하는 경향을 그래프를 통해 확인했으며, 실제 요약문에 있는 핵심 단어들이 요약 문장 안에 포함되었다.

3. Extractive 요약을 시도해 보고 Abstractive 요약 결과과 함께 비교해 보았다.
> 두 요약 결과를 문법완성도 측면과 핵심단어 포함 측면으로 나누어 비교하고 분석 결과를 표로 정리하여 제시하였다.


# PRT(Peer Review Template)


- [x]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**


> 문제에서 요구하는 최종 결과물이 첨부되었는지 확인
> 문제를 해결하는 완성된 코드란 프로젝트 루브릭 3개 중 2개, 퀘스트 문제 요구조건 등을 지칭
> 해당 조건을 만족하는 코드를 캡쳐해 근거로 첨부
1. Abstractive 모델 구성을 위한 텍스트 전처리 단계가 체계적으로 진행되었다. -> O
2. 텍스트 요약모델이 성공적으로 학습되었음을 확인하였다. -> O
3. Extractive 요약을 시도해 보고 Abstractive 요약 결과과 함께 비교해 보았다. -> X
                 
- [x]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**

> 해당 코드 블럭에 doc string/annotation이 달려 있는지 확인
> 해당 코드가 무슨 기능을 하는지, 왜 그렇게 짜여진건지, 작동 메커니즘이 뭔지 기술.
> 주석을 보고 코드 이해가 잘 되었는지 확인
> 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.

```python
threshold = 7
total_cnt = len(src_tokenizer.word_index) # 단어의 수
rare_cnt = 0 # 등장 빈도수가 threshold보다 작은 단어의 개수를 카운트
total_freq = 0 # 훈련 데이터의 전체 단어 빈도수 총 합
rare_freq = 0 # 등장 빈도수가 threshold보다 작은 단어의 등장 빈도수의 총 합

# 단어와 빈도수의 쌍(pair)을 key와 value로 받는다.
for key, value in src_tokenizer.word_counts.items():
    total_freq = total_freq + value

    # 단어의 등장 빈도수가 threshold보다 작으면
    if(value < threshold):
        rare_cnt = rare_cnt + 1
        rare_freq = rare_freq + value

print('단어 집합(vocabulary)의 크기 :', total_cnt)
print('등장 빈도가 %s번 이하인 희귀 단어의 수: %s'%(threshold - 1, rare_cnt))
print('단어 집합에서 희귀 단어를 제외시킬 경우의 단어 집합의 크기 %s'%(total_cnt - rare_cnt))
print("단어 집합에서 희귀 단어의 비율:", (rare_cnt / total_cnt)*100)
print("전체 등장 빈도에서 희귀 단어 등장 빈도 비율:", (rare_freq / total_freq)*100)
```
      
- [ ] **3. 에러가 난 부분을 디버깅하여 문제를 “해결한 기록을 남겼거나”, "새로운 시도 또는 추가 실험을 수행”해봤나요?**

        
> 문제 원인 및 해결 과정을 잘 기록하였는지 확인
> 문제에서 요구하는 조건에 더해 추가적으로 수행한 나만의 시도, 실험이 기록되어 있는지 확인
> 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.


- [x] **4. 회고를 잘 작성했나요?**


> 주어진 문제를 해결하는 완성된 코드 내지 프로젝트 결과물에 대해 배운점과 아쉬운점, 느낀점 등이 기록되어 있는지 확인
> 전체 코드 실행 플로우를 그래프로 그려서 이해를 돕고 있는지 확인
> 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.
```
"In this mission, I learned about two different summarization options: extractive summarization and\nabstract summarization. Although I'm still a bit confused about the seq2seq concept, I got experience in summarizing large data of language.\nAnd especially when dealing with recurrent dropout. It spend a lot of time this and also I'm curious about \nIt is possible to callbacks for early stopping and saving checkpoints simultaneously. "
```

- [x] **5. 코드가 간결하고 효율적인가요?**
 
> 파이썬 스타일 가이드 (PEP8) 를 준수하였는지 확인
> 하드코딩을 하지않고 함수화, 모듈화가 가능한 부분은 함수를 만들거나 클래스로 짰는지
> 코드 중복을 최소화하고 범용적으로 사용할 수 있도록 함수화했는지
> 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.

```python
def decode_sequence(input_seq):
    # 입력으로부터 인코더의 상태를 얻음
    e_out, e_h, e_c = encoder_model.predict(input_seq)

     # <SOS>에 해당하는 토큰 생성
    target_seq = np.zeros((1,1))
    target_seq[0, 0] = tar_word_to_index['sostoken']

    stop_condition = False
    decoded_sentence = ''
    while not stop_condition: # stop_condition이 True가 될 때까지 루프 반복

        output_tokens, h, c = decoder_model.predict([target_seq] + [e_out, e_h, e_c])
        sampled_token_index = np.argmax(output_tokens[0, -1, :])
        sampled_token = tar_index_to_word[sampled_token_index]

        if (sampled_token!='eostoken'):
            decoded_sentence += ' '+sampled_token

        #  <eos>에 도달하거나 최대 길이를 넘으면 중단.
        if (sampled_token == 'eostoken'  or len(decoded_sentence.split()) >= (headlines_max_len-1)):
            stop_condition = True

        # 길이가 1인 타겟 시퀀스를 업데이트
        target_seq = np.zeros((1,1))
        target_seq[0, 0] = sampled_token_index

        # 상태를 업데이트 합니다.
        e_h, e_c = h, c

    return decoded_sentence
```
  
# 참고 링크 및 코드 개선
```
# 코드 리뷰 시 참고한 링크가 있다면 링크와 간략한 설명을 첨부합니다.
# 코드 리뷰를 통해 개선한 코드가 있다면 코드와 간략한 설명을 첨부합니다.
```
