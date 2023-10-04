# AIFFEL Campus Online Code Peer Review Templete
- Coder : MyungJun Lee
- Reviewer : JeongHunLim


## 루브릭


1. 자기만의 카메라앱 기능 구현을 완수하였다.
> 얼굴 영역과 랜드마크를 정확하게 검출하고, 스티커 사진을 합성시키는 데 성공하였다.
3. 스티커 이미지를 정확한 원본 위치에 반영하였다.
> 정확한 좌표계산을 통해 고양이 수염의 위치가 원본 얼굴에 잘 어울리게 출력되었다.
4. 카메라 스티커앱을 다양한 원본이미지에 적용했을 때의 문제점을 체계적으로 분석하였다.
> 얼굴각도, 이미지 밝기, 촬영거리 등 다양한 변수에 따른 영향도를 보고서에 체계적으로 분석하였다.

# PRT(Peer Review Template)
- [ ]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**

  
> 문제에서 요구하는 최종 결과물이 첨부되었는지 확인
    - 네 잘 첨부되어 있습니다.
> 문제를 해결하는 완성된 코드란 프로젝트 루브릭 3개 중 2개, 퀘스트 문제 요구조건 등을 지칭
    - 네 잘 해결했습니다.
> 해당 조건을 만족하는 코드를 캡쳐해 근거로 첨부

#Road original image 
img_overlap = img_rgb_copy
#Define the sticker_area on the img_overlap image
sticker_area = img_overlap[refined_y:refined_y + img_sticker.shape[0], refined_x:refined_x + img_sticker.shape[1]]
#img_sticker.shape[0] is Height, img_sticker.shape[1] is Width
#Create a mask where the sticker is not white
mask = np.all(img_sticker != [255, 255, 255], axis=-1)
#Overlap two images using cv2.addWeighted (alpah is src1's weight, beta is src2's weight) 
sticker_area[mask] = cv2.addWeighted(src1=sticker_area[mask], alpha=0.6, src2=img_sticker[mask], beta=0.4, gamma=0)
plt.imshow(img_overlap)
plt.show()
                 
- [ ]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**

 
> 해당 코드 블럭에 doc string/annotation이 달려 있는지 확인
    - 네 잘 달려있습니다.
> 해당 코드가 무슨 기능을 하는지, 왜 그렇게 짜여진건지, 작동 메커니즘이 뭔지 기술.
    - 네 잘 짜여져있습니다. 잘 작성되어 있습니다
> 주석을 보고 코드 이해가 잘 되었는지 확인
    - 네 이해가 잘 됩니다
> 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.

#Utilize face region(nose) information
for dlib_rect, landmark in zip(dlib_rects, list_landmarks):
    print(landmark[30]) #The point of center of nose
    x, y = landmark[30][0], landmark[30][1] - dlib_rect.height()//2 #x of nose, 
    w, h = dlib_rect.width(), dlib_rect.height() #w: width of rectengle, h: height of rectangle
print(f'(x,y) : ({x},{y})')
print(f'(w,h) : ({w},{h})')




# Replace the sticker_area with the new sticker_area
img_overlap[refined_y:refined_y + img_sticker.shape[0], refined_x:refined_x + img_sticker.shape[1]] = sticker_area

           
- [ ] **3. 에러가 난 부분을 디버깅하여 문제를 “해결한 기록을 남겼거나”, "새로운 시도 또는 추가 실험을 수행”해봤나요?**

        
> 문제 원인 및 해결 과정을 잘 기록하였는지 확인
    - 네 잘 작성되어 있습니다.
> 문제에서 요구하는 조건에 더해 추가적으로 수행한 나만의 시도, 실험이 기록되어 있는지 확인
    - 추가적으로 overlap하는 방식을 사용했다.
> 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.
    
    sticker_area = img_overlap[refined_y:refined_y + img_sticker.shape[0], refined_x:refined_x + img_sticker.shape[1]]
    '''
            
- [ ]  **4. 회고를 잘 작성했나요?**


> 주어진 문제를 해결하는 완성된 코드 내지 프로젝트 결과물에 대해 배운점과 아쉬운점, 느낀점 등이 기록되어 있는지 확인
    - 네 잘 작성되어 있습니다.
> 전체 코드 실행 플로우를 그래프로 그려서 이해를 돕고 있는지 확인
    - 그런 부분은 없습니다.
> 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.

이번 과제는 실제 생활과 연관된 부분이 있어서 실제로 구현하는 과정이 나름 재미있었다. 
어려운 부분은 스티커 이미지가 4차원?으로 불러와지지가 않아서 노드의 코드대로만 작업을 수행했을 때, 
스티커의 흰색 부분이 투명해지지 않는 문제가 있었다.
이미지를 불러올 때, cv에서 png파일의 transparence 부분까지 불러오지 않는 것 같기도 하다
나는 흰색 부분에 마스크를 씌어서 원본과 겹치는 방법을 사용했다.(chatGPT에 물어봤다)
또 저장할 때, plt로 이미지가 제대로 보이더라도 cv로 저장하면 다시 RGB가 반전되어 보였다.
이 부분을 통해 plt와 cv가 이미지를 다루는 방법이 상이하다는 점을 알 수 있었다.
저장할 때, 결국 다시 색을 반전해줘야 하는 번거로움이 있었다.
끝!
'''



- [ ]  **5. 코드가 간결하고 효율적인가요?**

 
> 파이썬 스타일 가이드 (PEP8) 를 준수하였는지 확인
    - 일부 라인은 79자를 초과한다. 줄 바꿈으로 개선 필요
> 하드코딩을 하지않고 함수화, 모듈화가 가능한 부분은 함수를 만들거나 클래스로 짰는지
    - 이미지 경로가 하드코딩 되어 있다. 특정 기능을 수행하는 부분을 함수나 클래스로 만들지는 않았다.
> 코드 중복을 최소화하고 범용적으로 사용할 수 있도록 함수화했는지
    - 중복은 없습니다. 함수화가 된 부분은 없습니다.
> 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.

import os
import cv2
import matplotlib.pyplot as plt
import numpy as np
import dlib

  
# 참고 링크 및 코드 개선
```
# 코드 리뷰 시 참고한 링크가 있다면 링크와 간략한 설명을 첨부합니다.
# 코드 리뷰를 통해 개선한 코드가 있다면 코드와 간략한 설명을 첨부합니다.
- 수정은 안 했지만 아래와 같이 작성하면 더 간편할 것 같습니다

my_image_path = 'images/profile-mj.png'
model_path = 'models/shape_predictor_68_face_landmarks.dat'
sticker_path = os.getenv('HOME')+'/aiffel/camera_sticker/images/cat.png'

img_bgr = load_image(my_image_path)
dlib_rects, img_rgb = detect_face(img_bgr)
list_landmarks = get_landmarks(img_rgb, dlib_rects, model_path)
result_img = apply_sticker(img_rgb, list_landmarks, dlib_rects, sticker_path)

```
