# SVD란 무엇인가?

## 배경지식

1. 고유벡터 (Eigen Vector)
- **“벡터 x에 어떠한 선형변환 A를 했을 때, 그 크기만 변하고 원래 벡터와 평행한 벡터 x는 무엇인가요?”**

1. 고유값 (Eigen Value)
- **“그렇다면, 그 크기는 얼마만큼 변했나요?”**

![Untitled](SVD%E1%84%85%E1%85%A1%E1%86%AB%20%E1%84%86%E1%85%AE%E1%84%8B%E1%85%A5%E1%86%BA%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%80%E1%85%A1%20c9eddb155e3f4733b8111ed7ca2f40e4/Untitled.png)

AX=Xλ 즉 x라는 벡터에 A라는 행렬을 곱했더니 상수배(Eigen Value) 만큼 선형 변환이 이루어졌다는 뜻이다.

여기서 X를 알때 A와 λ를 구할수 있고 반대로 V를 알때 A, λ를 구할수 있음(Eigen decomposition)

SVD의 목적식인 $R=U\Sigma V^T$ 를 구할때 Eigen Decomposition이 사용됨.

1. orthogonal matrix
- 자기 자신을 제외한 모든 벡터와 직교하는 행렬

⇒ $A^TA=I=AA^T, A^{-1}=A^T$

## SVD

직교하는 벡터 집합(v1,v2)에 대해서 선형 변환 후 여전히 직교하는 벡터 집합은(u1, u2) 무엇인가?

⇒ 직교 벡터로 분해하는 이유는, 서로 가장 다른 vector들을 구해서 하나의 벡터가 하나의 정보만을 가지게 하기 위함.

$AV=U\Sigma$

$A=U\Sigma {V^-1}$

$U, V$ : orthogonal matrix

$\Sigma$ : diagonal matrix

Eigen Decomposition를 이용해서 $V, U, \Sigma$를 구하고, $V, U, \Sigma$의 일부분(Hyperparameter)만 이용해

서로 곱하여 예측값 A를 찾는다.

여기서 $\Sigma$의 값은 각각 $u_1 v_1$의 정보의 크기를 의미한다.

eg. 

![Untitled](SVD%E1%84%85%E1%85%A1%E1%86%AB%20%E1%84%86%E1%85%AE%E1%84%8B%E1%85%A5%E1%86%BA%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%80%E1%85%A1%20c9eddb155e3f4733b8111ed7ca2f40e4/Untitled%201.png)

각각의 U(user)가 각각의 B(book)에 대해 점수를 매긴 matrix가 있다고 하고,

빨간색 ? 를 구하고 싶으면 0으로 ?들을 채우고,  아래 수식

$A=U\Sigma {V^-1}$

       A가 위 그림의 matrix가 되는것이고 계산을 통해 $U, \Sigma, V$를 구한다.

그리고 $U, \Sigma, V$의 일부분을 추출해서 서로 곱한다.

그러면 새로운 A가 만들어지는데 이 A가 예측값이 되는것이다.