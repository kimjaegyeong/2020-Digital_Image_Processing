
Image Transfer
=============

## 1. Style Transfer 을 사용하여 자기 사진을 고흐 스타일로 변환해 본 소감
원본 이미지에 또 다른 이미지를 필터처럼 씌워 혼합된 이미지를 만들어내는 것은 카메라 애플리케이션에서 지원하는 필터 등으로 익숙해져 있었는데, 실제 코드를 보고 직접 구동해보는 것은 새로운 감각이었습니다. colab이 제공하는 라이브러리와 주피터 노트북을 이용하여 간단히 Styel Transfer을 수행할 수 있다는 것이 저번시간까지는 체감이 되지 않았습니다.   
그래서 colab을 사용하지 않는 방법을 찾아보니 colab과 같이 라이브러리를 제공하지 않는 경우에는 직접 다운하고, 학습시켜야 하는 데에 굉장히 오래 걸린다는 것을 알았습니다. 이번 실습을 통해서 colab의 편리성이 확실히 와닿았습니다.   
또, 이번 실습에 사용된 라이브러리인 텐서플로우에 대해서 조금 검색해봤는데, 텐서플로우는 구글이 제공하는 라이브러리이며 머신러닝 분야에서 가장 많이 사용되는 라이브러리라는 사실을 알았습니다. 이번에 사용된 것은 텐서플로우 라이브러리중에 pre-trained VGG network이고, 이것은 이미지 변환 네트워크를 학습하는 방법입니다.    
새로운 이미지를 변환할 때 학습된 이미지 변환 네트워크에 대해 feed-forward만 하면 되어 재학습이 필요 없고 실시간 변환이 가능함을 알았습니다. 아직까지는 Style Transfer의 코드가 어떻게 작동하는 것인지, 어떤 기능을 하는 함수를 이용하여 만든 것인지는 잘 모르지만 디지털 영상처리를 열심히 공부하면 깨닫는 날이 올 것이라 생각합니다. 
