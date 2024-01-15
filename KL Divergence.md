Kullback_Leibler Divergence

KL(Kullback-Leibler) divergence는 두 확률 분포 사이의 차이를 측정하는 데 사용되는 통계적인 개념입니다. 이는 정보 이론과 확률 분포 분석에서 중요한 개념 중 하나입니다. KL divergence는 두 확률 분포가 얼마나 비슷한지 또는 다른지를 측정합니다.

두 확률 분포 P(x)와 Q(x)가 주어졌을 때, KL divergence는 다음과 같이 정의됩니다:
$$D_{KL}(P\,||\,Q) = \sum_x \,\textrm P(x){log}\frac{P(x)}{Q(x)}dx$$
또는 연속 확률 변수인 경우 :
$$D_{KL}(P\,||\,Q) = \int \textrm P(x){log}\frac{P(x)}{Q(x)}dx$$

여기서 $D_{KL}(P \,||\,Q)$ 는 P에서 Q로의 KL divergence를 나타냅니다. 이 값이 클수록 두 분포는 서로 다르다는 것을 의미하며, 값이 작을수록 두 분포는 비슷하다고 볼 수 있습니다.

KL divergence는 비대칭적이기 때문에, $D_{KL}(P \,||\,Q)$ 와 $D_{KL}(Q \,||\,P)$ 는 일반적으로 다를 수 있습니다. 또한, KL divergence가 0이면 두 분포가 완전히 동일하다는 의미입니다.