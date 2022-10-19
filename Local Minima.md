# Local Minima

날짜: 2022/10/14
상태: 딥러닝

> Local Minima 문제에도 불구하고 딥러닝이 잘 되는 이유는?
> 
> - GD가 Local Minima 문제를 피하는 방법은?
> - 찾은 해가 Global Minimum인지 아닌지 알 수 있는 방법은?

**고차원의 공간에서는 Local Minima는 아주 드문 현상이다. 그 이유는 모든 축의 방향에서 오목한 형태가 형성될 확률이 거의 없기 때문에 딥러닝이 잘 이루어진다.** 

*** 모든 weight가 local minima에 빠져야 weight update가 정지된다.

- **Local Minima** :  일부 범위에서의 극소값 만족
    - weight값이 계속해서 변화가 없다면 minima에 도달
    - gradient vanishing

↔ Critical Point : 1차 미분이 0인 지점, 극값

↔ Saddle Point : 방향에 따라 극대값이자 극소값인 지점

![https://github.com/boostcamp-ai-tech-4/ai-tech-interview/blob/main/answers/img/3-deep-learning/critical-saddle-point-and-local-minima.png?raw=true](https://github.com/boostcamp-ai-tech-4/ai-tech-interview/blob/main/answers/img/3-deep-learning/critical-saddle-point-and-local-minima.png?raw=true)

### 추가 질문

- GD가 Local Minima 문제를 피하는 방법은?
    
    ⇒ GD를 발전시킨 방법으로 gloabl minima를 찾는다.
    
    - **SGD(Stochasitc GD) :** 1개 이상의 데이터를 확인한 후, 방향 결정 ****
    - **Momentum** : 이전 gradient의 방향성(관성) 이용
    - **NAG(Nesterov Accelerated Gradient) :** look-ahead gradient(모멘텀과 유사) 활용, 먼저 1스텝 나아가본 후 결정
    - **Adagrad :** gradient의 변화율을 제곱하여 더해주는 방법, G→♾️, W→0
    - **Adadelta :** Exponential Moving Area(EMA)를 활용하여 AdaGrad 보완
        
        ***  EMA : 이전 변화량에 특정 비율 곱해 더하는 인자
        
    - **RMSprop :** G부분을 합이 아닌 지수평균으로 바꾸어 Adagrad를 보완
    - **Adam :** G의 지수평균을 저장(Momentum)+ G의 제곱값의 지수평균을 저장(RMSProp)

- 찾은 해가 Global Minimum인지 아닌지 알 수 있는 방법은?
    - GD의 경우, gloabl minima 도달이 보장되어 있지 않다.
    - 고차원의 경우, local minima가 드물기 때문에 local minima로 의심된다면 global minima일 가능성이 높다.
    

(참고)

[https://github.com/boostcamp-ai-tech-4/ai-tech-interview/blob/main/answers/3-deep-learning.md#14](https://github.com/boostcamp-ai-tech-4/ai-tech-interview/blob/main/answers/3-deep-learning.md#14)

[https://www.quora.com/How-do-I-overcome-a-local-minimum-problem-in-neural-networks](https://www.quora.com/How-do-I-overcome-a-local-minimum-problem-in-neural-networks)
