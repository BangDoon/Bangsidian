Evidence of Lower Bound
Variational Lower Bound
Proxy Loss

ELBO는 Variational Inference(변분 추론)에서 사용되는 중요한 개념 중 하나입니다. Variational Inference은 확률 분포를 근사화하고, 관심 있는 확률 분포를 찾기 위해 다른 분포를 사용하는 방법론 중 하나입니다. ELBO는 Evidence Lower Bound의 약자로, 이를 통해 원래의 로그 가능도를 더 간단하게 다룰 수 있게 해줍니다.

ELBO는 다음과 같은 관계를 가집니다:
$$ logP(x) = KL(q(z) \, \Vert \, P(z \, \vert \, x)) + ELBO $$

여기서$logP(x)$는 데이터의 로그 가능도이고, KL(�(�)∥�(�∣�))KL(q(z)∥P(z∣x))는 변분 분포 �(�)q(z)와 사후 분포 �(�∣�)P(z∣x) 간의 KL divergence입니다. 마지막으로 ELBOELBO는 Evidence Lower Bound를 나타냅니다.