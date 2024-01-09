Progressive Growing of GANs
[[GAN]]

styleGAN의 기초가 되는 모델

## Abstract

기존의 GAN 에는 이미지가 고해상도 일수록 생성자가 판별자를 속이기 어려워 지고, 학습 속도도 매우 느려졌으며, 학습이 불안정한 문제점이 있었습니다. 이를 해결하기 위한 방법으로 본 논문에서는 이름에서 볼 수 있듯이 생성자(generator) 와 판별자(discriminator)를 점진적으로 학습 시키는 방법을 제안합니다.


## Progressive Growing of GANs

![[pggan1.gif]]
