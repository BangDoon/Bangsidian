Generative Adersarial Nets
[[Image, Dimension, and Distribution]]
[[CNN]]

## 1. Introduction

- 딥러닝의 작동방식은 여러 데이터(사진, 오디오,파형 등)에 대해서 모집단에 근사하는 확률분포를 나타내는 다양한 계층적 모델을 발견하는 것입니다. 지금까지는 고차원의 방대한 데이터를 클래스 레이블에 매핑해서 구분하는 모델을 사용했습니다. 모델은 well-behaved gradient를 가지는 선형 활성화 함수들을 사용한 역전파, 드롭아웃 알고리즘을 기반으로 하고 있습니다.

- 지금까지 Deep generative model들은 MLE(maximum likelihood estimation) 그리고 관련된 전략들에서 발생하는 많은 확률 연산들의 근사치를 내는데 발생하는 어려움이 있고, 앞서 말한 분류 모델에서 주로 사용하던 선형 활성화 함수들을 사용하기 어려움이 있기 때문에 크게 주목 받지 못했습니다.

이 논문에서는 이러한 한계점을 회피하는 Generative model 을 제시하고 있습니다.

- 이 논문에서 소개되는 adversarial nets 프레임워크의 핵심은 generative model(생성 모델)과 discriminative model(판별 모델)을 경쟁시키는 것입니다. 생성 모델은 실제 데이터 분포와 유사하게 fake 데이터를 생성하게 되고, 판별 모델은 샘플 데이터가 생성 모델이 생성한 fake 데이터 인지, 실제 데이터인지 판별하는 것을 학습하게 됩니다.

- 이 프레임워크(adversarial nets)에 사용되는 generative model 과 discriminative model 모두 다중 퍼셉트론으로 이루어진 딥러닝 모델이라서, 일반적으로 사용되는 다양한 딥러닝 테크닉들을 모두 사용할 수 있습니다.


## 3. Adversarial nets

adversarial modeling 프레임워크는 두 모델 모두 다층 퍼셉트론이 적용됩니다.

![[Pasted image 20240110000600.png]]

G=generative model , D=discriminator 를 뜻하고 D(input) 이 1에 가까울수록 정확도가 높은 것입니다. 위 수식을 해석하면,


- 첫번째 항 : 실제 데이터 x를 discriminator에 넣었을 때 나오는 결과를 log 취했을 때 얻는 기댓값
  $$ E_{x \sim P_{data}(x)}[logD(x)] $$


- 두번째 항 : generator가 만든 fake data를 discriminator가 판단한 결과를 log(1-결과)한 기댓값

$$ E_{z\sim p_z(z)}[log(1-D(G(z)))] $$

이 수식은 Discriminator의 입장에서와 Generator의 입장, 이렇게 두가지로 해석할 수 있습니다.

먼저 D의 입장에서는 G가 만들어낸 Fake data와 실제 데이터의 구분이 완벽하게 이루어 지는게 이상이므로, 수식에 적용해보면, 첫번째 항에서는 완벽하게 실제데이터로 판단하여 log1이 되서 0이 되고, 두번째 항에서는 완벽하게 구분해내어 D(G(z))가 0이 되기 때문에 log(1-0) 즉, log1이 되므로 0이됩니다. 따라서 D의 입장에서 가장 이상적인 V(D,G)의 값은 최대값인 0 임을 알 수 있습니다.

다음으로 G의 입장에서는 자신이 만들어낸 데이터와 실제데이터를 D가 전혀 구별하지 못하는 것이 이상이므로, 수식에 적용하여 보면, 첫번째 항은 관련이 없기 때문에 넘어가고, 두번째 항에서 D가 G의 fake data를 모두 진짜라고 판단하여, D(G(z))가 1이 나오게 되면 log0이 되므로 음의 무한대가 됩니다. 따라서 G의 입장에서 가장 이상적인 V(D,G)의 값은 최솟값인 음의 무한대 임을 알 수 있습니다.

정리하자면, D는 V(D,G)를 최대화 하기 위해이고, G는 V(D,G)를 최소화 하기 위해 학습하게 됩니다. 이를 수식으로 나타내어 아래와 같이 되는 것입니다.
![[Pasted image 20240110000649.png|150x50]]

![[Pasted image 20240110000710.png]]

위 그림은 GAN의 학습과정을 나타내고 있습니다.

(a) : 학습 초기에는 Real data와 Fake data의 분포가 전혀 다른것을 확인 할 수 있고, D의 성능도 요동치며 흔들리는 모습을 볼 수 있습니다.

(b) : D가 (a)때 처럼 요동치지않고 어느정도 안정이 된 것을 볼 수 있습니다. 이는 D의 성능이 좋아졌음을 보여줍니다.

(c) : 이번에는 Fake data의 분포가 점점 Real data의 분포에 가까워지고 있음을 보여줍니다. 이는 G의 성능이 좋아졌음을 보여줍니다.

(d) : 앞의 과정의 반복의 결과로 Real data와 Fake data는 구분이 어려울 정도로 유사해졌고, D의 정답확률이 1/2가 됩니다.
















