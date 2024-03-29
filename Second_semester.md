
 1.딥러닝 
=============

###  Feature extraction
머신러닝에서 컴퓨터가 스스로 학습하려면, 즉 컴퓨터가 입력받은 데이터를 분석하여 일정한 패턴이나 규칙을 찾아내려면 사람이 인지하는 데이터를 컴퓨터가 인지할 수 있는 데이터로 변환해 주어야 합니다. 이때 데이터별로 어떤 특징을 가지고 있는지를 찾아내고, 그것을 토대로 데이터를 벡터로 변환하는 작업을 특징추출(feature extraction)이라고 합니다.

### classification
데이터가 어느 범주(Category)에 속하는지를 판단하는 방법입니다.

###  인공신경망(ANN)
신경망이란 인간의 뇌가 가지는 생물학적 특성 중 뉴런의 연결 구조를 가리키며, 이러한 신경망을 본떠 만든 네트워크 구조를 인공신경망(Artificial Neural Network, ANN)이라고 부릅니다.
하나의 뉴런은 다른 뉴런에게서 신호를 받고 또 다른 뉴런에게 신호를 전달하는 단순한 역할만을 수행합니다. 하지만 인간의 뇌는 이러한 수많은 뉴런이 모여 만든 신호의 흐름을 기반으로 다양한 사고를 할 수 있게 되며, 이것을 컴퓨터로 구현하도록 노력한 것이 바로 인공신경망입니다.
인공신경망은 입력층을 통해 학습하고자 하는 데이터를 입력받고, 입력된 데이터들은 여러 단계의 은닉층을 지나면서 처리가 이루어집니다. 처리가 이루어진 데이터들은 출력층을 통해 최종 결과로 출력되게 됩니다. 
이러한 신경망을 3개 이상 중첩한 구조를 깊은 신경망(Deep Neural Network, DNN)이라고 부릅니다.

### 퍼셉트론(perceptron)
인공 신경망 이론을 설명한 최초의 알고리즘입니다. 
가장 간단한 퍼셉트론으로, 입력층과 출력층만으로 구성된 단층 퍼셉트론의 개념이 있습니다. 
단층 퍼셉트론(single layer perceptron)이 동작하는 방식은 다음과 같습니다.   
`1. 각 노드의 입력치와 가중치를 서로 곱하여 모두 합한다.`   
`2. 이렇게 합한 값을 활성화 함수가 가지고 있는 임계치(선택의 기준이 되는 값)와 서로 비교한다.`   
`3. 만약 그 값이 임계치보다 크면 뉴런은 활성화되고, 만약 임계치보다 작으면 뉴런은 비활성화 된다.`   

 2.텐서플로우
=============
### 그래프: 노드와 꼭짓점으로 연결되어 있는 객체. 
연산에 필요한 것들을 분별할 수 있는 구조가 그래프입니다. 
### 1. 노드
수학적인 연산 동작(Operation : + - * / )을 의미합니다.
### 2. 엣지(꼭짓점)
엣지는 다차원 데이터 배열(텐서)을 의미합니다.
### 3. 오퍼레이션
그래프 상의 노드를 오퍼레이션이라고 부르며 오퍼레이션은 하나 이상의 텐서를 받는다. 오퍼레이션은 연산을 수행하고, 결과를 하나 이상의 텐서로 반환(Return)할 수 있습니다.
### 4. 텐서
텐서는 일종의 다차원 배열로서 내부적으로 모든 데이터는 텐서를 통해 표현된다. 그래프 내의 오퍼레이션 간에는 텐서만이 전달됩니다.
### 5. 세션
텐서플로우 작동 방식:
모든 것을 파이썬에서 설계 후
외부에서 연산 <- 연산을 실행시키는 곳이 세션이다.
즉 CPU, GPU 위에서 연산이 실행되고 세션은 텐서플로우 계산을 할 수 있도록 환경을 만들어주는 것입니다.
### 6. 변수
변수는 그래프를 실행할 때 파라메터를 저장하고 갱신하는데 사용하며 메모리 상에서 텐서를 저장하는 버퍼 역할을 합니다.   

### placeholder
학습용 데이터를 담는 그릇으로 실행 시점에 데이터를 할당합니다.

3.캐라스
=============
### 전처리: 데이터를 다루기 쉬운 형태로 변환시키는 과정
Tokenizer(): 토큰화와 단어에 대한 인덱싱(정수 인코딩)을 위해 사용됩니다.
pad_sequence(): 모델의 입력으로 사용하려면 모든 샘플의 길이를 동일하게 맞추어야할 때가 있습니다. 이를 자연어 처리에서는 패딩(padding) 작업이라고 하는데, 보통 숫자 0을 넣어서 길이가 다른 샘플들의 길이를 맞춰줍니다.   
케라스에서는 pad_sequence()를 사용합니다. pad_sequence()는 정해준 길이보다 길이가 긴 샘플은 값을 일부 자르고, 정해준 길이보다 길이가 짧은 샘플은 값을 0으로 채웁니다.   
`첫번째 인자 = 패딩을 진행할 데이터`   
`maxlen = 모든 데이터에 대해서 정규화 할 길이`   
`padding = 'pre'를 선택하면 앞에 0을 채우고 'post'를 선택하면 뒤에 0을 채움.`   
### 워드 임베딩: 텍스트 내의 단어들을 밀집 벡터로 만드는 것 (대부분의 값이 실수이고, 상대적으로 저차원인 밀집 벡터(dense vector))
Embedding() : Embedding()은 단어를 밀집 벡터로 만드는 역할을 합니다. 인공 신경망 용어로는 임베딩 층(embedding layer)을 만드는 역할을 합니다. Embedding()은 정수 인코딩이 된 단어들을 입력을 받아서 임베딩을 수행합니다.   
`첫번째 인자 = 단어 집합의 크기. 즉, 총 단어의 개수`   
`두번째 인자 = 임베딩 벡터의 출력 차원. 결과로서 나오는 임베딩 벡터의 크기`   
`input_length = 입력 시퀀스의 길이`   
모델링(Modeling):  
Sequential() : 인공 신경망의 입력층, 은닉층, 출력층을 구성하기 위해 사용됨   
Sequential()을 model로 선언한 뒤에 model.add()라는 코드를 통해 층을 단계적으로 추가   
Embedding()을 통해 생성하는 임베딩 층(embedding layer) 또한 인공 신경망의 층의 하나이므로 model.add()로 추가   
Dense() : 전결합층(fully-conntected layer)을 추가합니다. model.add()를 통해 추가할 수 있습니다.   
`첫번째 인자 = 출력 뉴런의 수.`   
`input_dim = 입력 뉴런의 수. (입력의 차원)`   
`activation = 활성화 함수.`   
`- linear : 디폴트 값으로 별도 활성화 함수 없이 입력 뉴런과 가중치의 계산 결과 그대로 출력. Ex) 선형 회귀`   
`- sigmoid : 시그모이드 함수. 이진 분류 문제에서 출력층에 주로 사용되는 활성화 함수.`   
`- softmax : 소프트맥스 함수. 셋 이상을 분류하는 다중 클래스 분류 문제에서 출력층에 주로 사용되는 활성화 함수.`   
`- relu : 렐루 함수. 은닉층에 주로 사용되는 활성화 함수.`   
summary() : 모델의 정보를 요약해서 보여줍니다.   
### 컴파일(Compile)과 훈련(Training):
compile() : 모델을 기계가 이해할 수 있도록 컴파일 합니다. 오차 함수와 최적화 방법, 메트릭 함수를 선택할 수 있습니다.   
optimizer : 훈련 과정을 설정하는 옵티마이저를 설정합니다. 'adam'이나 'sgd'와 같이 문자열로 지정할 수도 있습니다.   
loss : 훈련 과정에서 사용할 손실 함수(loss function)를 설정합니다.  
metrics : 훈련을 모니터링하기 위한 지표를 선택합니다.   
fit() : 모델을 학습합니다. 모델이 오차로부터 매개 변수를 업데이트 시키는 과정을 학습, 훈련, 또는 적합(fitting)이라고 하기도 하는데, 모델이 데이터에 적합해가는 과정이기 때문입니다. 그런 의미에서 fit()은 모델의 훈련을 시작한다는 의미를 가지고 있습니다.   
`첫번째 인자 = 훈련 데이터에 해당됩니다.`   
`두번째 인자 = 지도 학습에서 레이블 데이터에 해당됩니다.`   
`epochs = 에포크. 에포크 1은 전체 데이터를 한 차례 훑고 지나갔음을 의미함. 정수값 기재 필요. 총 훈련 횟수를 정의합니다.`   
`batch_size = 배치 크기. 기본값은 32. 미니 배치 경사 하강법을 사용하고 싶지 않을 경우에는 batch_size=None을 기재합니다.`   
validation_data(x_val, y_val) = 검증 데이터(validation data)를 사용합니다. 검증 데이터를 사용하면 각 에포크마다 검증 데이터의 정확도도 함께 출력되는데, 이 정확도는 훈련이 잘 되고 있는지를 보여줄 뿐이며 실제로 모델이 검증 데이터를 학습하지는 않습니다. 검증 데이터의 loss가 낮아지다가 높아지기 시작하면 이는 과적합(overfitting)의 신호입니다.   
validation_split= validation_data 대신 사용할 수 있습니다. 검증 데이터를 사용하는 것은 동일하지만, 별도로 존재하는 검증 데이터를 주는 것이 아니라 X_train과 y_train에서 일정 비율을 분리하여 이를 검증 데이터로 사용합니다. 역시나 훈련 자체에는 반영되지 않고 훈련 과정을 지켜보기 위한 용도로 사용됩니다. 아래는 validation_data 대신에 validation_split을 사용했을 경우를 보여줍니다.   
verbose = 학습 중 출력되는 문구를 설정합니다.   
`- 0 : 아무 것도 출력하지 않습니다.`   
`- 1 : 훈련의 진행도를 보여주는 진행 막대를 보여줍니다.`   
`- 2 : 미니 배치마다 손실 정보를 출력합니다.`   
### 평가(Evaluation)와 예측(Prediction):
evaluate() : 테스트 데이터를 통해 학습한 모델에 대한 정확도를 평가합니다.   
`첫번째 인자 = 테스트 데이터에 해당됩니다.`   
`두번째 인자 = 지도 학습에서 레이블 테스트 데이터에 해당됩니다.`   
`batch_size = 배치 크기.`   
  
predict() : 임의의 입력에 대한 모델의 출력값을 확인합니다.   
`첫번째 인자 = 예측하고자 하는 데이터.`
`batch_size = 배치 크기.`   

### 모델의 저장(Save)과 로드(Load):
save() : 인공 신경망 모델을 hdf5 파일에 저장합니다.   
load_model() : 저장해둔 모델을 불러옵니다.   

4.얼굴인식
=============
face landmarks: 이미지에서 얼굴만 분리한 후 얼굴의 특징점을 추출합니다.   
```
img = cv2.imread(path) path 읽어오기
(h,w) = img.shape[:2] 이미지의 높이, 넓이 읽고 저장
width = 500           
ratio = width / float(w) 
height = int(h * ratio)
return cv2.resize(img,(width,height)) 이미지 비율 맞춰주기
known_encodings = [] 
known_names = []
known_dir = 'known' 디렉터리 path 지정
for file in os.listdir(known_dir): 
  img = read_img(known_dir + '/' + file) path에서 이미지를 모두 읽어옴
  img_enc = face_recognition.face_encodings(img)[0] 얼굴 인코딩
  known_encodings.append(img_enc) 
  known_names.append(file.split('.')[0])
print(known_names) 모든 known 라벨을 출력
unknown_dir = 'unknown' 디렉터리 path 지정
for file in os.listdir(unknown_dir):
 print("Processing",file)
 img = read_img(unknown_dir + '/' + file) 이미지를 모두 읽어옴
 img_enc = face_recognition.face_encodings(img)[0] 인코딩 진행
 results = face_recognition.compare_faces(known_encodings,img_enc)
Known 인코딩한 사진과 Unknown 인코딩한 사진을 비교
 print(face_recognition.face_distance(known_encodings,img_enc))
인식률을 출력 
```
5.Fashion 10개 인식
=============
### 필터 (Filter)
필터는 그 특징이 데이타에 있는지 없는지를 검출해주는 함수입니다. 

### 컨볼루셔널 레이어  (Convolutional Layer)  
컨볼루셔널 레이어는 입력 데이타로 부터 특징을 추출하는 역할을 합니다.   
컨볼루셔널 레이어는 특징을 추출하는 기능을 하는 필터(Filter)와, 이 필터의 값을 비선형 값으로 바꾸어 주는 액티베이션 함수(Activiation 함수)로 이루어집니다.   

### Max pooling (맥스 풀링)
맥스 풀링은 Activation map을 MxN의 크기로 잘라낸 후, 그 안에서 가장 큰 값을 뽑아내는 방법입니다.   

<img width="444" alt="2121E641583ED6AF23" src="https://user-images.githubusercontent.com/50646904/99941528-817f5880-2db1-11eb-9eca-2f38e9937faf.png">   

그림은 4x4 Activation map에서 2x2 맥스 풀링 필터를 stride를 2로 하여 2칸씩 이동하면서 맥스 풀링을 한 예인데, 좌측 상단에서는 6이 가장 큰 값이기 때문에 6을 뽑아내고, 우측 상단에는 2,4,7,8 중 8 이 가장 크기 때문에 8을 뽑아 내었습니다.   

### Dense Layer
다층 퍼셉트론 신경망에서 입력과 출력을 모두 연결해주는 레이어이다. 입럭 뉴련이 4개, 출력 뉴런이 8개이면 총 연결선은 32개가 된다. 연결선은 가중치를 포함하고 있는데, 연결강도를 의미합니다.    
가중치가 높을 수록 해당 입력 뉴런이 출력 뉴런에 미치는 영향이 큽니다.   

6.숫자인식
=============
### flatten layer 
Convolution Layer나 Max Pooling Layer 를 반복적으로 거치면 주요 특징만 추출되고 추출된 주요 특징은 전결합층에 전달되어 학습됩니다.   
전결합층에 전달하기 위해 1차원 자료로 바꿔주는데 이때 사용되는 Layer입니다.
### 액티베이션 함수
relu: 입력값이 0보다 작으면 0이고 0보다 크면 입력값 그대로를 내보냅니다.    
softmax: 여러개의 분류를 가질 수 있는 함수이고, 각 요소의 확률의 합산 값은 항상 1입니다.    
sigmoid: 결과 값에 따라 참 또는 거짓을 나타내는 함수입니다.   

### dropout layer
Fully conneted 네트워크와 softmax 함수 중간에서 오버피팅을 막기 위해 사용되는 layer입니다.   
뉴럴 네트워크가 학습중일때 랜덤하게 뉴런을 꺼서 학습을 방해하여 학습이 학습용 데이터에 치우치는 현상을 방지합니다.    


참고
=============
https://ukayzm.github.io/facial-landmarks/   
https://www.tensorflow.org/js/tutorials/training/handwritten_digit_cnn   
https://tykimos.github.io/2018/09/30/Hello_Fashion_MNIST/   
https://ssongnote.tistory.com/13   
https://bcho.tistory.com/1149   
https://wikidocs.net/32105   
https://dsbook.tistory.com/14?category=761052   
https://rosinality.github.io/2017/05/%ED%8A%B9%EC%A7%95-%EC%B6%94%EC%B6%9Cfeature-extraction%EA%B3%BC-%EB%94%A5-%EB%9F%AC%EB%8B%9D/   
