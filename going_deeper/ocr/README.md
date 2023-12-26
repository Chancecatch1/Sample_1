
# AIFFEL Campus Online Code Peer Review Templete
- Coder : MyungJun Lee
- Reviewer : Dong Hee Lee


## 루브릭


1. Text recognition을 위해 특화된 데이터셋 구성이 체계적으로 진행되었다.
> 텍스트 이미지 리사이징, ctc loss 측정을 위한 라벨 인코딩, 배치처리 등이 적절히 수행되었다.
2. CRNN 기반의 recognition 모델의 학습이 정상적으로 진행되었다.
> 학습결과 loss가 안정적으로 감소하고 대부분의 문자인식 추론 결과가 정확하다.
3. keras-ocr detector와 CRNN recognizer를 엮어 원본 이미지 입력으로부터 text가 출력되는 OCR이 End-to-End로 구성되었다.
> 샘플 이미지를 원본으로 받아 OCR 수행 결과를 리턴하는 1개의 함수가 만들어졌다.


# PRT(Peer Review Template)


- [x]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**

> 문제에서 요구하는 최종 결과물이 첨부되었는지 확인
> 문제를 해결하는 완성된 코드란 프로젝트 루브릭 3개 중 2개, 퀘스트 문제 요구조건 등을 지칭
> 해당 조건을 만족하는 코드를 캡쳐해 근거로 첨부

> 1. Text recognition을 위해 특화된 데이터셋 구성이 체계적으로 진행되었다. -> O
> 2. CRNN 기반의 recognition 모델의 학습이 정상적으로 진행되었다.-> O
> 3. keras-ocr detector와 CRNN recognizer를 엮어 원본 이미지 입력으로부터 text가 출력되는 OCR이 End-to-End로 구성되었다. -> X


                 
- [x]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**


> 해당 코드 블럭에 doc string/annotation이 달려 있는지 확인
> 해당 코드가 무슨 기능을 하는지, 왜 그렇게 짜여진건지, 작동 메커니즘이 뭔지 기술.
> 주석을 보고 코드 이해가 잘 되었는지 확인
> 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.

```python
from PIL import ImageDraw
from IPython.display import display

def detect_text(img_path):
    # 이미지를 열고 배열로 변환합니다.
    result_img = Image.open(img_path)
    img_array = np.array(result_img)

    # 차원을 확장하여 배치 형태로 만듭니다.
    img_batch = np.expand_dims(img_array, axis=0)

    # OCR로 텍스트 영역을 탐지합니다.
    ocr_result = detector.detect(images=img_batch)[0]

    # 이미지에 그리기 위한 객체를 생성합니다.
    img_draw = ImageDraw.Draw(result_img)
    
    # 감지된 텍스트 영역을 시각화하고 잘라냅니다.
    cropped_imgs = []
    for text_result in ocr_result:
        img_draw.polygon(text_result, outline='red')
        x_min = text_result[:,0].min() - 5
        x_max = text_result[:,0].max() + 5
        y_min = text_result[:,1].min() - 5
        y_max = text_result[:,1].max() + 5
        word_box = [x_min, y_min, x_max, y_max]
        cropped_imgs.append(result_img.crop(word_box))

    # 수정된 이미지와 잘린 이미지들을 반환합니다.
    return result_img, cropped_imgs

# 함수를 호출하고 결과를 표시합니다.
img_pil, cropped_img = detect_text(image_path)
display(img_pil)

```
      
- [x] **3. 에러가 난 부분을 디버깅하여 문제를 “해결한 기록을 남겼거나”, "새로운 시도 또는 추가 실험을 수행”해봤나요?**

        
> 문제 원인 및 해결 과정을 잘 기록하였는지 확인
> 문제에서 요구하는 조건에 더해 추가적으로 수행한 나만의 시도, 실험이 기록되어 있는지 확인
> 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.

샘플이미지 외에 새로운 이미지 시도
```python
image_path_wasabi = HOME_DIR + '/wasabi.jpg'
img_wasabi, cropped_img = detect_text(image_path_wasabi)
display(img_wasabi)
```

- [x] **4. 회고를 잘 작성했나요?**


> 주어진 문제를 해결하는 완성된 코드 내지 프로젝트 결과물에 대해 배운점과 아쉬운점, 느낀점 등이 기록되어 있는지 확인
> 전체 코드 실행 플로우를 그래프로 그려서 이해를 돕고 있는지 확인
> 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.

> 회고
> 주어진 코드를 이해하는것만으로 학습시간을 다 쓴 것 같다, 물론 전체를 다 이해하진 못했지만 OCR이 어떻게 진행되는지는 어렴풋이 알 수 있었다.

- [x] **5. 코드가 간결하고 효율적인가요?**

 
> 파이썬 스타일 가이드 (PEP8) 를 준수하였는지 확인
> 하드코딩을 하지않고 함수화, 모듈화가 가능한 부분은 함수를 만들거나 클래스로 짰는지
> 코드 중복을 최소화하고 범용적으로 사용할 수 있도록 함수화했는지
> 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.

```python
from PIL import ImageDraw
from IPython.display import display

def detect_text(img_path):
    # 이미지를 열고 배열로 변환합니다.
    result_img = Image.open(img_path)
    img_array = np.array(result_img)

    # 차원을 확장하여 배치 형태로 만듭니다.
    img_batch = np.expand_dims(img_array, axis=0)

    # OCR로 텍스트 영역을 탐지합니다.
    ocr_result = detector.detect(images=img_batch)[0]

    # 이미지에 그리기 위한 객체를 생성합니다.
    img_draw = ImageDraw.Draw(result_img)
    
    # 감지된 텍스트 영역을 시각화하고 잘라냅니다.
    cropped_imgs = []
    for text_result in ocr_result:
        img_draw.polygon(text_result, outline='red')
        x_min = text_result[:,0].min() - 5
        x_max = text_result[:,0].max() + 5
        y_min = text_result[:,1].min() - 5
        y_max = text_result[:,1].max() + 5
        word_box = [x_min, y_min, x_max, y_max]
        cropped_imgs.append(result_img.crop(word_box))

    # 수정된 이미지와 잘린 이미지들을 반환합니다.
    return result_img, cropped_imgs

# 함수를 호출하고 결과를 표시합니다.
img_pil, cropped_img = detect_text(image_path)
display(img_pil)
```
  
# 참고 링크 및 코드 개선
```
# 코드 리뷰 시 참고한 링크가 있다면 링크와 간략한 설명을 첨부합니다.
# 코드 리뷰를 통해 개선한 코드가 있다면 코드와 간략한 설명을 첨부합니다.
```
