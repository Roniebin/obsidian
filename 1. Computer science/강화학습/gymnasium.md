# gym 시작하기

Gym은 강화학습 알고리즘을 개발하고 비교평가하는 툴킷입니다. Gym은 에이전트를 만들 때 특정한 가정을 요구하지 않을 뿐만 아니라, TensorFlow나 Theano와 같은 라이브러리와도 호환됩니다.

gym 라이브러리는 테스트 문제들, 즉 강화학습을 연습해 볼 수 있는 다양한 환경을 모아놓은 것입니다. 이 환경들은 공통 인터페이스를 가지고 있어서 범용 알고리즘을 작성하는 데 도움을 줍니다.

------------

**설치하기**

시작하기 전에, 컴퓨터에 파이썬 3.5 이상이 깔려 있어야 합니다. 다음으로는 pip을 사용하여 다음과 같이 gym을 설치합니다:

pip install gym

------------

**소스 코드를 이용하여 빌드하기**

원한다면 gym의 Git repository를 바로 복제해서 가져올 수 있습니다. 이 방법은 Gym 자체를 수정하거나 원하는 환경을 추가할 때 특히 유용합니다. 다음 코드를 이용해서 다운로드받고 이용하면 됩니다:

git clone https://github.com/openai/gym

cd gym

pip install -e

이후에는 pip install -e .[all] 을 실행하여 모든 환경에 대한 내용을 담은 [전체 버전 설치](https://github.com/openai/gym#installing-everything)를 할 수 있습니다. 이를 위해서는 cmake나 최신 [pip](https://github.com/openai/gym#pip-version) 버전 등 관련된 몇 가지를 더 설치해야 합니다.

--------------
