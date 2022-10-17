# one-shot learning

# 배경

## 뉴럴넷의 한계

- 사람은 처음 보는 물건에 대해 조금만 봐도 다른 물건과 구분할 수 있다.
- 하지만 뉴럴넷은 새로운 물건을 구분하기 위해 많은 데이터를 학습해야 한다.

# One-Shot Learning

- 새로운 레이블을 구분하기 위해 필요한 훈련 데이터가 적을 때도 모델이 좋은 성능을 낼 수 있게 만드는 방법
    - 이때, 이미 다른 레이블에 대해 충분히 훈련한 **pretrained** 모델이 있어야 한다.
- pretrained 모델은 새로운 레이블을 받아도 데이터의 특성에 대한 기존 학습을 바탕으로 분류할 수 있다.

## Siamese network

[http://www.cs.cmu.edu/~rsalakhu/papers/oneshot1.pdf](http://www.cs.cmu.edu/~rsalakhu/papers/oneshot1.pdf)

- **`Distance Fucntion`**을 이용해 이미지를 구분한다. 이 때, 이미지가 어떤 것인지 구분하는게 아니라 **다른 이미지와 동일한지** 여부를 판단하는 방식
    - `Nearest Neighborhood`와 아이디어가 비슷

$$
D(x_1, x_2) = degree\ of\ difference images
$$

- $D(x_1, x_2) <= k$인 경우 같은 사람이라고 분류
- $D(x_1, x_2) > k$인 경우 다른 사람이라고 분류