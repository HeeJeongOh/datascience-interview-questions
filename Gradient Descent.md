> Gradient Descent에 대해서 쉽게 설명한다면?
> 
> - 왜 꼭 Gradient를 써야 할까? 그 그래프에서 가로축과 세로축 각각은 무엇인가? 실제 상황에서는 그 그래프가 어떻게 그려질까?
> - GD 중에 때때로 Loss가 증가하는 이유는?
> - Back Propagation에 대해서 쉽게 설명 한다면?

**Gradient Descent (경사하강법) : 손실함수의 최솟값을 근사적으로 알아내기 위한 방법**

- 손실함수(loss) : 정답(y)과 예측값(y^) 사이의 오차를 표현하는 함수
    - MSE (Mean Sqaure Error) : 평균제곱오차
    - CE (Cross Entropy ) : 실제 분포를 알지 못할 때, 모델링을 통해 구해진 분포 p를 통해 모분포 q 예측
        - Bineary CE :  0과 1 사이의 확률값 반환
        - Categorical CE : one-hot 벡터 반환
    
- 손실함수를 미분하여 기울기가 절댓값이 작아지는 방향으로 지점을 이동해가며, 손실함수의 최솟값을 구하기
    - 전체 데이터를 모두 학습시킨 후, 가중치 업데이트
    - 가로축 , 세로축(오차값,cost), 보폭(=learning rate), 그래프(도식)
        
- 순전파, 역전파
    - 순전파 : 입력에 대한 모델 결과 계산
    - 역전파 :  forward과정을 통해 나온 오차를 활용해 각 layer의 W, b 최적화        
        ㄴ 파라미터들에 대한 그래디언트 계산 (각각의 w에 대해 loss)        
        ㄴ 각각의 가중치 행렬 W(l)에 대해 손실함수에 대한 미분 계산
        
    ```python
    # forward 
    y_pred = M.forward(batch_in.view(-1, 28*28).to(device))
    
    # cost
    loss_out = loss(y_pred,batch_out.to(device))
    
    # backward
    optm.zero_grad()      # reset gradient 
    loss_out.backward()   # backpropagate 
    optm.step()           # optimizer update
    
    ```
    
### 추가 질문

- 그냥 f’(x) = 0이 되는 x를 구하면 되지 않는가 ?
    - 간단한 예제에서도 변수의 개수가 10개 이상 ⇒ 일반적인 계산으로 x 구하기 어려움
- GD 중에 때때로 Loss가 증가하는 이유 ? (깃헙)
    - 현재 있는 위치가 local mininal 여서 주위에서 다른 곳으로 가다가 loss 가 올라가는 경우
    - step size 가 커서 그냥 건너 뛰다 더 작은 loss 값에 도달하지 못하는 경우



*** 확률적 경사하강법 (SGD) ⇒ N개의 데이터만 골라 학습하여 가중치 갱신 <배치사이즈>

ㄴ 모든 학습데이터를 한번에 다루는 것 → 시간이 오래 걸리고 부작용 존재
