Unpaired Image-to-Image Translation(CycleGAN)
[[GAN]]


기존의 GAN은 학습을 위한 완벽한 데이터 쌍이 필요하다는 한계점이 있었습니다. 이러한 한계점을 보완하기 위해 cycleGAN이 등장하였습니다.

# 1. cycle-consistency loss : 사이클-일관성 손실
---

cycleGAN은 핵심 아이디어는 이름에서 알 수 있듯이 사이클(cycle)을 구성하는 것 입니다. 한 도메인에서 다른 도메인으로 변환하고 다시 반대로 변환합니다.

도메인 A 사진(x)을 도메인 B로 변환하고, 다시 도메인 A로 변환(x^)합니다. 이 사이클이 이상적으로 진행된다면 원래 사진(x)와 재구성된 사진(x^)은 동일할 것입니다. 두 사진이 동일하지 않다면 픽셀 수준에서 손실을 측정하여 아래와 같이 **cycle-consistency loss**를 구합니다.

![[Pasted image 20240110163216.png]]

사이클에서는 두개의 생성자가 필요합니다. 도메인 A 에서 도메인 B로 생성하는 G_{AB} = G 와 도메인 B에서 도메인 A로 생성하는 G_{BA} = F 가 있습니다. 따라서 cycle-consistency loss 또한 두 개를 가집니다.

