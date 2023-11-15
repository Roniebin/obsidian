---
tags: ComputerScience, 머신러닝
---
# CNN이란 무엇인가?

- Convolutional neural network(CNN 또는 ConvNet)란 **데이터로부터 직접 학습하는 딥러닝의 신경망 아키텍처**

- 이미지를 분석하기 위한 패턴을 찾는데 유용한 알고리즘
- 이미지를 직접 학습하고 패턴을 사용해 이미지를 분류한다.
- CNN은 기존에 image 인식에 사용하던 FCNN(Fully Connected Neural Network)이 가지고 있는 한계를 개선하기 위해 개발되었다.

------------------

### FCNN의 어떤문제?

FCNN은 input image를 픽셀의 행으로 직렬화 한 후, 이것을 입력 신호로 주는 방식으로 동작한다.

이러한 방식은 직렬화를 수행하는 과정에서 <mark style="background: #FF5582A6;">데이터의 형상이 무시된다는 문제점</mark>이 있다.

<mark style="background: #FF5582A6;">픽셀은 주변 픽셀과 관련이 있는데 fully connected layer에 집어넣기 위해 직렬화를 수행하면서 이러한 상관관계들을 잃게된다.</mark>

때문에 데이터의 전체 관계를 고려하지 못하게 된다는 문제점이 있다.

<mark style="background: #FF5582A6;">
CNN은 이러한 문제점을 해결하기 위해 fully connected layer 앞부분에 convolution layer와 pooling layer를 추가했다</mark>.

![[Pasted image 20231111143605.png]]

-----------------------

### convolution layer

convolution layer는 <mark style="background: #FF5582A6;">입력 데이터로부터 특징을 추출</mark>하는 역할을 한다.
convolution layer는 특징을 추출하는 기능을 하는 filter와
이 filter의 값을 비선형 값으로 바꾸어 주는 activation function(활성화 함수) 으로 이루어져있다.

--------------------------
#### filter

filter는 그 특징이 data에 있는지 없는지를 검출해주는 함수이다.
예를 들어 곡선을 검출해주는 필터가 있다고 하자.
필터는 왼쪽 그림처럼 행렬로 정의될 것이다.

-----------------------------
#### convolution

![[Pasted image 20231111144224.png]]

filter를 원본 이미지에 적용하는 방식이 convolution 이다.
convolution은 필터를 일정 간격으로 이동시키면서 input data에 연산을 적용시키는 것을 말한다.
이 일정한 간격을 stride라고 한다.
그리고 필터를 적용해서 얻어낸 결과를 feature map이라고 한다.

이런 식으로 이미지 전체를 보는 것이 아니라 부분을 보는 것이 CNN의 핵심 아이디어라고 할 수 있다.

--------------------------------
#### padding

![[Pasted image 20231111144424.png]]


nput data에 필터를 적용한 내용을 보면 필터를 적용한 후의 크기가 필터 적용 전보다 작아진다는 것을 알 수 있다.

CNN에서는 여러 개의 convolution layer를 거치면서 필터를 적용 시키는데, 점점 결과 값이 작아지게 되면 처음에 비해서 output 이미지가 너무 작아지게 되기 때문에 이것을 방지하기 위해서 사용되는 것이 padding이다.

padding은 입력 이미지 가장자리에 특정 값으로 설정된 픽셀을 추가함으로써 입력 이미지와 출력 이미지 크기를 같거나 비슷하게 만드는 역할을 한다.

그리고 edge나 모서리 부분의 픽셀 정보도 충분히 활용할 수 있게 하는 역할도 하고있다.

padding 적용 전에는 모서리 픽셀 정보는 딱 한번밖에 이용되지 않는데, 만약 모서리 부분 픽셀에 중요한 정보가 담겨있다면? convolution 과정에서 정보가 유실되는 문제가 발생한다.

CNN에서는 주로 제로 패딩을 이용하는데 이미지의 가장자리에 0값을 갖는 픽셀을 추가하는 것을 제로 패딩이라고 한다.

--------------------------
#### activation function

![[Pasted image 20231111144449.png]]

filter들을 통해서 feature map이 추출되었다면 이 feature map에 활성화 함수를 적용하게 된다.

특징이 있는지 없는지 filter를 통해 추출한 값이 정량적인 값으로 나오는데, 너무 크거나 필요 없거나 튀는 데이터가 있을 수도 있기 때문에 데이터의 폭을 어느정도 조절해서 그 특징이 있을 가능성, 없을 가능성 이렇게 비선형값으로 바꾸어주는 과정이 필요하다. 이 때 쓰이는 함수가 activation 함수이다.

그 종류로는 계단함수, 시그모이드 함수, Tanh 함수, Relu함수 등이 있다.

------------------

### pooling layer

![[Pasted image 20231111144627.png]]

convolution layer를 거쳐 나온 feature map 에서 <mark style="background: #FF5582A6;">모든 데이터가 필요하지는 않다</mark>.
고해상도 사진을 보고 물체를 판별할 수 있지만 저해상도 사진으로도 어떤 사진인지 판별할 수 있는 것과 같은 원리다.
판단에는 적당량의 데이터만 있어도 된다.
<mark style="background: #FF5582A6;">pooling layer를 거치면서 적당히 이미지 크기도 줄이고 특정 feature만 강조하게 된다</mark>.

<mark style="background: #FF5582A6;">추출된 activation map을 인위로 줄이는 이 작업을 pooling 혹은 sub-sampling이라고 한다.</mark>

pooling에는 여러가지 방법이 있는데, 어떠한 값을 대표값으로 두는지에 따라서 average, max, min pooling이 있다.

그 중 max pooling 기법이 많이 사용된다. CNN이 신경세포와 유사한 방식을 취하기 때문. 신경세포학적으로 보면 통상적으로 강한 신호만 전달되고 나머지는 무시한다.

-----------------------

![[Pasted image 20231111144937.png]]

앞에서 convolution layer와 pooling layer를 통해 feature들을 뽑아냈다면
이 추출된 feature 값을 fully connected layer를 통해 분류작업을 한다.