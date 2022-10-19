# Cost Function과 Activation Function은 무엇인가요

![Untitled](Cost%20Function%E1%84%80%E1%85%AA%20Activation%20Function%E1%84%8B%E1%85%B3%E1%86%AB%20%E1%84%86%E1%85%AE%E1%84%8B%E1%85%A5%E1%86%BA%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%80%E1%85%A1%E1%84%8B%2008b46a3c2a104b86bd66da36bdda6587/Untitled.png)

Loss Function 과 Cost Function은 **원래의 값과 가장 오차가 작은 가설함수**를 도출하기 위해 사용되는 함수입니다.

**<Loss Function>**

input(x)에 대한 예측값(y^)과 실제 label값(y) 사이의 오차를 계산하는 함수이다.

예로 linear regression의 경우 Loss function으로 최소제곱오차를 사용한다.

![Untitled](Cost%20Function%E1%84%80%E1%85%AA%20Activation%20Function%E1%84%8B%E1%85%B3%E1%86%AB%20%E1%84%86%E1%85%AE%E1%84%8B%E1%85%A5%E1%86%BA%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%80%E1%85%A1%E1%84%8B%2008b46a3c2a104b86bd66da36bdda6587/Untitled%201.png)

**즉, 하나의 input data에 대해서 오차를 계산하는 함수를 Loss function이라고 한다.**

**<Cost Function>**

모든 input dataset에 대해서 오차를 계산하는 함수를 Cost function이라고 한다.

따라서 Cost function은 모든 input dataset에 대해 계산한 Loss function의 평균 값으로 구할 수 있다.

![Untitled](Cost%20Function%E1%84%80%E1%85%AA%20Activation%20Function%E1%84%8B%E1%85%B3%E1%86%AB%20%E1%84%86%E1%85%AE%E1%84%8B%E1%85%A5%E1%86%BA%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%80%E1%85%A1%E1%84%8B%2008b46a3c2a104b86bd66da36bdda6587/Untitled%202.png)

Logistic Regression에서 사용하는 Loss function이다.

![Untitled](Cost%20Function%E1%84%80%E1%85%AA%20Activation%20Function%E1%84%8B%E1%85%B3%E1%86%AB%20%E1%84%86%E1%85%AE%E1%84%8B%E1%85%A5%E1%86%BA%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%80%E1%85%A1%E1%84%8B%2008b46a3c2a104b86bd66da36bdda6587/Untitled%203.png)

위 Loss function에 상응하는 Cost function이다. 모든 data에 대한 Loss를 평균내어 Cost를 계산할 수 있다.

**<Objective Function>**

학습을 통해 최적화시키려는 함수이다. 딥러닝에서는 일반적으로 학습을 통해 Cost를 최소화시키는 optimize작업을 수행을 하고 이때 Cost function을 Objective function이라 볼 수 있다. 하지만 Objective function에 꼭 Cost function만 있는 것은 아니다. 예로 MLE와 같이 학습을 통해 확률을 최대화하려는 function 역시 Objective function으로 정의되지만 이는 Cost, Loss function은 아니다.

**<Activation Function>**

linear function만으로는 non-linear한 모델을 표현할 수 없기 때문에 activation function을 통과 시킴으로써 

non-linear한 함수를 만들기 위함.

![Untitled](Cost%20Function%E1%84%80%E1%85%AA%20Activation%20Function%E1%84%8B%E1%85%B3%E1%86%AB%20%E1%84%86%E1%85%AE%E1%84%8B%E1%85%A5%E1%86%BA%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%80%E1%85%A1%E1%84%8B%2008b46a3c2a104b86bd66da36bdda6587/Untitled%204.png)