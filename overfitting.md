# overfitting

![Untitled](overfitting%201e48ea9fb70f4e8e86a9a37807ab7180/Untitled.png)

- Train acc는 올라가는데 Test acc는 내려가는 현상
- Low Bias, High Variance
- 잘못된 Local minimum에 빠져버리는 현상

# 해결법

1. more augmentation
- 조금 더 복잡한 train set으로 학습시켜 좀 더 일반화된 특징들을 찾기위함.

![Untitled](overfitting%201e48ea9fb70f4e8e86a9a37807ab7180/Untitled%201.png)

- Data augmentation techniques are **used to generate additional, synthetic data using the data you have**
. Augmentation methods are super popular in computer vision applications but they are just as powerful for NLP. (nlp augmentation)

- k-fold / ensamble

train set을 ex) 5조각으로 나누어 1조각을 validation fold 나머지를 training fold로 구분해

5개의 모델을 만들어서 inference에서 합치는 방법.

![Untitled](overfitting%201e48ea9fb70f4e8e86a9a37807ab7180/Untitled%202.png)

- drop-out

몇몇의 weight를 학습에 사용하지 않음으로써(every step마다 바뀜) 좀더 일반화된 특징을 잡기 위한 방법

![Untitled](overfitting%201e48ea9fb70f4e8e86a9a37807ab7180/Untitled%203.png)

- more data

좀 더 많은 데이터로 일반화된 특징을 잡기위한 방법.