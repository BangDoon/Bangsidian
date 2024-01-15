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

- 이미지($X_{0}$ )가 완전한 Gaussian Noise($X_{T}$ )가 될 때까지 Gaussian Noise를 점진적으로 추가하는 Markov Process
- 현재 이미지가 주어졌을 때 1초 뒤 이미지는 평균이 $\sqrt{1- \beta_{t}}X_{t-1}$ , 분산이 $\beta_{t}I$ 인 Gaussian의 분포를 따른다.
- $X_{t} = \sqrt{1- \beta_{t}}X_{t-1} + \sqrt{\beta_{t}}\epsilon$ , $\epsilon \sim N(0,I)$ 
- $\epsilon$ 은 이미지와 같은 차원의 랜덤 노이즈 

![[Pasted image 20240115210910.png]]

- Diffusion 에서 Foward Process를 설명할 때, 사전 정의된 Timestep 만큼, T 번 Forward Process 를 수행하면 이미지는 Isotropic Gaussian(완전한 노이즈) 로 수렴해야 한다고 정의
- 이를 만족하는 Noise Schedule 이라는 $\beta$ 값의 집합을 정의

![[Pasted image 20240115211329.png]]

- T=0 의 이미지로부터 T=500 까지 가려면 Forward Process 를 500번 수행 -> 비효율적임
- Noise Schedule 을 수식적으로 다시 정리하여 한번에 수행 가능하게 변환
- Noise Schedul 의 의미는 Forward process를 진행할 수록
	1. 이미지 분포의 평균은 0에 근접하도록
	2. 이미지 분포의 분산은 1에 근접하도록
	즉, Normal Gaussian 이 되도록

![[Pasted image 20240115211558.png]]

![[Pasted image 20240115211822.png]]


### Reverse Process
-  Gaussian Noise($X_{T}$ )에서 점진적으로 Gaussian Noise를 제거하여 이미지($X_{0}$ )를 복원하는 Markov Process
- DD