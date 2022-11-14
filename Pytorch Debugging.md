# Pytorch Debugging

> TF, PyTorch 등을 사용할 때 디버깅 노하우는?
> 
> - PyTorch에 대해

**vscode 사용 시, 각종 debugging extension 활용할 수 있다.**

- Hinterland : 코드 및 변수 자동완성 기능
- Autopep8: 자동 코드정리기능
- Variable Inspector : 변수들을 트래킹

**TensorBoard, wandb를 활용하여 logging을 확인할 수 있다.**

[https://tutorials.pytorch.kr/recipes/recipes/tensorboard_with_pytorch.html](https://tutorials.pytorch.kr/recipes/recipes/tensorboard_with_pytorch.html)

.

.

### 추가설명

**Pytorch (머신러닝 라이브러리)**

- Dynamic Computation graphs (↔ TF: Static )
- Define by Run : 실행을 하면서 그래프를 생성해가는 방식 ⇒ 결과를 즉시 확인할 수 있음
- **[Tensor(텐서)](https://tutorials.pytorch.kr/beginner/blitz/tensor_tutorial.html#sphx-glr-beginner-blitz-tensor-tutorial-py)**
    - Numpy의 ndarray와 유사
    - GPU나 다른 연산 가속을 위한 특수 하드웨어에서 실행 가능
 
- **torch.autograd** (pytorch를 쓰는 가장 큰 이유)
    - Autograd에서 미분을 진행하는 방법
       
        : 매개변수(parameter)의 .grad 속성(attribute)에, 모델의 각 매개변수에 대한 변화도(gradient)를 계산하고 저장
        
    
      ```python
      import torch

      # requires_grad=True : autograd 에 모든 연산(operation)들을 추적할 것
      a = torch.tensor([2., 3.], requires_grad=True)
      b = torch.tensor([6., 4.], requires_grad=True)

      Q = 3*a**3 - b**2

      # gradient 인자(argument)를 명시적으로 전달
      # gradient : Q모양의 tensor, Q에 대한 gradient 의미 (?)
      external_grad = torch.tensor([1., 1.])
      Q.backward(gradient=external_grad)
      ```
    
    - NN(Neural Network) : 중첩된 함수들의 모음
        - Forward Propagation : 신경망의 정답을 맞추는 과정, 최선의 추측
        - Backward Propagation : 추측값에서 오류에 따라 매개변수 조절
            - 오류에 대한 함수들의 매개변수들의 gradient 수집 → backward()
            - gradient descent를 사용하여 매개변수 최적화 → step()
    
    
      ```python
      # forward
      predict = model(data)

      loss = (predict - labels).sum()

      # backward 실행 
      loss.backward()

      # gradient descent
      optim.step()
      ```
    

  ↔ tensorflow에서 미분값을 저장하는 방법 : [Gradient Tape](https://www.tensorflow.org/api_docs/python/tf/GradientTape)

.

.

(참고)

[https://boostdevs.gitbook.io/ai-tech-interview/interview/3-deep-learning#10](https://boostdevs.gitbook.io/ai-tech-interview/interview/3-deep-learning#10)

[https://tutorials.pytorch.kr/beginner/blitz/autograd_tutorial.html#sphx-glr-beginner-blitz-autograd-tutorial-py](https://tutorials.pytorch.kr/beginner/blitz/autograd_tutorial.html#sphx-glr-beginner-blitz-autograd-tutorial-py)
