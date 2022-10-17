# Weight Initialization

- Weight Initialization 방법에 대해 말해주세요. 그리고 무엇을 많이 사용하나요?

### **초기 가중치 설정 (weight initialization)**

딥러닝 학습에 있어 초기 가중치 설정은 매우 중요한 역활을 한다. 가중치를 잘못 설정할 경우 기울기 소실 문제나 표현력의 한계를 갖는 등 여러 문제를 야기하게 된다. 또한 딥러닝의 학습의 문제가 non-convex 이기 때문에 초기값을 잘못 설정할 경우 local minimum에 수렴할 가능성이 커지게 된다.

초기값 설정을 잘못해 문제가 발생하는 경우들을 살펴보자.

**1) 초기값을 모두 0으로 설정한 경우**

만약 데이터를 평균 0정도로 정규화시킨다면, 가중치를 0으로 초기화 시킨다는 생각은 꽤 합리적으로 보일 수 있다. 그러나 실제로 0으로 가중치를 초기화 한다면 모든 뉴런들이 같은 값을 나타낼 것이고, 역전파 과정에서 각 가중치의 update가 동일하게 이뤄질 것이다. 이러한 update는 학습을 진행 해도 계속해서 발생할 것이며, 결국 제대로 학습하기 어려울 것이다. 또한 이러한 동일한 update는 여러 층으로 나누는 의미를 상쇄시킨다.

**2) 활성화 함수로 sigmoid 사용시 정규 분포 사용**

sigmoid함수는 input의 절대값이 조금이라도 커지게 되면 미분값이 소실되는 문제가 발생한다. 이 경우에 평균 0이고 표준편차가 1인 정규분포를 따르도록 가중치를 랜덤하게 초기화 한다고 가정하자.

이 경우에는 표준편차가 크기 때문에 학습을 반복할 수록 가중치 값들이 0,1 로 치우치는 문제 발생한다.(Gradient Vanishing) 이 경우 물론 Activation Function을 바꿈으로써 해결 할 수도 있겠지만, 가중치 초기화를 잘 설정함으로써도 어느정도 해결할 수 있다.

**3) 2의 case에서 표준편차를 줄였을 경우**

2의 문제를 확인하고 표준편차가 커 |x|값이 커지면서 기울기가 소실되는 문제를 확인했기 때문에, 표준편차를 줄여서

|x|값을 줄이려는 생각을 가지고 표준편차를 0.01로 설정한다고 가정하자. 이 경우에는 또다른 문제가 발생한다.

[https://t1.daumcdn.net/cfile/tistory/993C01365AB6262903](https://t1.daumcdn.net/cfile/tistory/993C01365AB6262903)

이렇게 표준편차를 적게 하면 층이 깊어질 수록 가중치 값들이 중간 값인 0.5 부근에 몰리는 문제를 확인할 수 있을 것이다.

따라서 이렇게 가중치를 설정하는 것만으로도 학습의 큰영향을 끼친다는 것을 확인할 수 있었다. 그렇다면 더 나은 학습을 위해 가중치를 초기화하는 여러 방법들에 대해서 알아보도록 한다.

**1. LeCun Initialization**

정규분포를 따르는 방법과 균등분포를 따르는 두가지 방법

([LeCun 98, Efficient Backprop](http://yann.lecun.com/exdb/publis/pdf/lecun-98b.pdf))

- LeCun Normal Initialization

![스크린샷 2022-10-14 오후 2.38.15.png](Weight%20Initialization%2035a19ac402fc4e769a26f81a165bcdb6/%25EC%258A%25A4%25ED%2581%25AC%25EB%25A6%25B0%25EC%2583%25B7_2022-10-14_%25EC%2598%25A4%25ED%259B%2584_2.38.15.png)

(n_in : 이전 layer(input)의 노드 수)

- LeCun Uniform Initialization

![스크린샷 2022-10-14 오후 2.38.57.png](Weight%20Initialization%2035a19ac402fc4e769a26f81a165bcdb6/%25EC%258A%25A4%25ED%2581%25AC%25EB%25A6%25B0%25EC%2583%25B7_2022-10-14_%25EC%2598%25A4%25ED%259B%2584_2.38.57.png)

(n_in : 이전 layer(input)의 노드 수)

**2. Xavier Initialization**

Xavier Initialization 혹은 Glorot Initialization라고도 불리는 초기화 방법은 이전 노드와 다음 노드의 개수에 의존하는 방법이다. Uniform 분포를 따르는 방법과 Normal분포를 따르는 두가지 방법이 사용된다.

구조는 LeCun의 초기화 방법과 유사하지만 다음 층의 노드 수도 사용하고, 많은 연구를 통해 가장 최적화된 상수값 또한 찾아냈다.

([Glorot & Bengio, AISTATS 2010](http://jmlr.org/proceedings/papers/v9/glorot10a/glorot10a.pdf))

- Xavier Normal Initialization

![스크린샷 2022-10-14 오후 2.40.15.png](Weight%20Initialization%2035a19ac402fc4e769a26f81a165bcdb6/%25EC%258A%25A4%25ED%2581%25AC%25EB%25A6%25B0%25EC%2583%25B7_2022-10-14_%25EC%2598%25A4%25ED%259B%2584_2.40.15.png)

(n_in : 이전 layer(input)의 노드 수, n_out : 다음 layer의 노드 수)

- Xavier Uniform Initialization

![스크린샷 2022-10-14 오후 2.41.19.png](Weight%20Initialization%2035a19ac402fc4e769a26f81a165bcdb6/%25EC%258A%25A4%25ED%2581%25AC%25EB%25A6%25B0%25EC%2583%25B7_2022-10-14_%25EC%2598%25A4%25ED%259B%2584_2.41.19.png)

(n_in : 이전 layer(input)의 노드 수, n_out : 다음 layer의 노드 수)

- Xaiver함수는 비선형함수(ex. sigmoid, tanh)에서 효과적인 결과를 보여준다. 하지만 ReLU함수에서 사용 시 출력 값이 0으로 수렴하게 되는 현상을 확인 할 수 있다. 따라서 ReLU함수에는 또 다른 초기화 방법을 사용해야 한다.

**3.He Initialization**

ReLU를 활성화 함수로 사용 시 Xavier 초기값 설정이 비효율적인 결과를 보이는 것을 확인했는데, 이런 경우 사용하는 초기화 방법을 He initialization이라고 한다. 이 방법 또한 정규분포와 균등분포 두가지 방법이 사용된다.([He et al. ,2015](http://arxiv.org/abs/1502.01852))

- He Normal Initialization

![스크린샷 2022-10-14 오후 2.42.47.png](Weight%20Initialization%2035a19ac402fc4e769a26f81a165bcdb6/%25EC%258A%25A4%25ED%2581%25AC%25EB%25A6%25B0%25EC%2583%25B7_2022-10-14_%25EC%2598%25A4%25ED%259B%2584_2.42.47.png)

(n_in : 이전 layer(input)의 노드 수)

- He Uniform Initialization

![스크린샷 2022-10-14 오후 2.42.58.png](Weight%20Initialization%2035a19ac402fc4e769a26f81a165bcdb6/%25EC%258A%25A4%25ED%2581%25AC%25EB%25A6%25B0%25EC%2583%25B7_2022-10-14_%25EC%2598%25A4%25ED%259B%2584_2.42.58.png)

(n_in : 이전 layer(input)의 노드 수)

---

### **Bias 초기화**

가중치 초기화 뿐만 아니라 편향(bias) 초기값 또한 초기값 설정 또한 중요하다.보통의 경우에는 Bias는 0으로 초기화 하는 것이 일반적이다. ReLU의 경우 0.01과 같은 작은 값으로 b를 초기화 하는 것이 좋다는 보고도 있지만 모든 경우는 아니라 일반적으로는 0으로 초기화 하는 것이 효율적이다.

### **Conclusion**

다양한 종류의 초기화 방법에 대해서 알아 보았다. 초기값 설정이 학습과정에 매우 큰 영향을 끼칠 수 있기 때문에 초기화 방법 또한 신중히 선택해야 한다.

- Sigmoid, tanh 경우 Xavier 초기화 방법이 효율적이다.
- ReLU계의 활성화 함수 사용 시 He 초기화 방법이 효율적이다.
- 최근의 대부분의 모델에서는 He초기화를 주로 선택한다.

마지막으로, 대부분의 초기화 방법이 Normal Distribution과 Uniform Distribution을 따르는 두가지 방법이 있는데 이에대한 선택 기준에 대해서는 명확한 것이 없다. 하지만 He의 논문의 말을 인용하면,

> 최근의 Deep CNN 모델들은 주로 Gaussian Distribution을 따르는 가중치 초기화 방법을 사용한다.
> 

따라서 Deep CNN의 경우 보통의 Gaussian 초기화 방법을 사용해 볼 수 있다.하지만 여러 초기화 방법들을 테스트하며 사용하는 것이 가장 좋은 방법일 것이다.