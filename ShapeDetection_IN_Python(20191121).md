디지털영상처리
=============
과제5: 사각형, 삼각형, 원의 모멘텀(또는 다른 방법)으로 도형을 인식하기.

1. 도형 검출 방법
[0] OpenCV를 사용하기 위해서 import cv2 한다. 
[1] 사용할 이미지를 cv2.imread를 이용하여 컬러로 읽어와 img에 저장한다.
[2] img에 저장한 사진을 cv2.cvtColor를 이용하여 흑백으로 변환한 뒤 gray에 저장한다.
[3] 흑백이 된 이미지를 threshold를 이용해 이진화하여 img_binaray에 저장한다. 이때 검출할 도형이 흰색영역, 배경이 검정색영역이어야한다. 
[4]  cv2.findContours로 이진화 영상에서 윤곽선을 검출한다. 이때 검색방법 중 cv2.RETR_EXTERNAL를 사용하면 도형 내부에 있는 윤곽선은 검출하지 않고, 오로지 외부의 윤곽선만을 검출한다. 근사화 방법 중  cv2.CHAIN_APPROX_NONE를 사용하면 다른 근사화 방법을 사용하는 것보다 검출되는 윤곽선의 구성점 개수를 줄일 수 있다.  예를 들어 직선을 검출할 때 그 직선의 양 끝점만을 저장하도록 한다. 
[5] 도형의 윤곽선을 검출한 뒤 표시를 위해 drawContours로 검출된 도형에게 보라색에 굵기가 2인 선을 덧씌운다. 
[6] 검출한 윤곽선을 직선으로 근사화 시키기 위해 approxPolyDP함수를 사용한다. 이 함수를 사용하면 APPROX_NONE을 사용해서 검출한 양 끝점을 서로 이어서 직선 1개로 변경할 수 있다. 
[7] 직선의 개수를 corner에 저장하고, if문을 이용하여 corner의 개수를 Label로 도형에 붙여준다. 
 
-------------
2. 소스코드
    
```
import cv2
def setLabel(img, str, contour):
    
    x,y,width,height = cv2.boundingRect(str)
    pt1 = (x,y)
    pt2 = (x+width, y+height)
    cv2.putText(img, contour, (pt1[0], pt2[1]), cv2.FONT_HERSHEY_SIMPLEX, 2, (255,0,255), 3, 8)

img = cv2.imread("C:/Users/k/Desktop/test4.png", cv2.IMREAD_COLOR)
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
ret,img_binary = cv2.threshold(gray, 0, 255, cv2.THRESH_OTSU)


contours,_= cv2.findContours(img_binary, cv2.RETR_EXTERNAL, cv2.CHAIN_APPROX_NONE)
for i in range(len(contours)):
    cv2.drawContours(img, [contours[i]], 0, (255, 0, 255), 2)
    
for cont in contours:
    
    approx = cv2.approxPolyDP(cont, cv2.arcLength(cont,True)*0.02, True)
    corner= len(approx)

    if corner== 3: setLabel(img,cont,'3')

    elif corner== 4: setLabel(img, cont, '4')

    elif corner== 5: setLabel(img,cont,'5')

    elif corner== 6: setLabel(img,cont,'6')

    else : setLabel(img,cont,'0')

    cv2.imshow('img',img)
    cv2.waitKey(0)
}
```
-------------
3. 결과 영상

-------------
