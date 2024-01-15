Denoising Diffusion Probabilistic Models


# Intro
---
- Diffusion (확산)은 액체나 기체에 다른 물질이 섞이고, 그것이 조금씩 번져가다 마지막엔 일률적인 농도로 바뀌는 현상

![[Pasted image 20240115193432.png]]


- 2015년 논문 "Deep unsupervised learning using nonequilibrium thermodynamics" 에서 Diffusion을 최초로 딥러닝으로 모델링 함

- 2020년 논문 "Denoising Diffusion Probabilistic Models"에서 딥러닝으로 모델링 된 Diffusion을 이미지 도메인에 적용
- 핵심 아이디어 : 점진적으로 물질이 퍼져 나가는 과정이 학습이 된다면, 반대과정도 가능하지 않을까?





# Process
---
**Foward Process** : 이미지($X_{0}$ )가 완전한 Gaussian Noise($X_{T}$ )가 될 때까지 Gaussian Noise를 점진적으로 추가하는 Markov Process
**Reverse Process** :  Gaussian Noise($X_{T}$ )에서 점진적으로 Gaussian Noise를 제거하여 이미지($X_{0}$ )를 복원하는 Markov Process

![[Pasted image 20240115194739.png]]

### Foward Process


