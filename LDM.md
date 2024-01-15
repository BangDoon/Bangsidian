Latent Diffusion Models

[[DDPM]]
[[CFG]]


- LDM의 특정 모델인 Stable Diffusion 
- 학습하는데 약 8억 정도(256개의 A100GPU로 150,000시간 동안 학습)가 들었지만 Open source 로 모델 공개
- 생성모델의 대중화를 선도, LDM 기반의 다양한 연구들이 진행
- Diffusion Model 의 앞/뒤에 Autoencoder 를 추가하여 샘플링 시 계산 비용을 대폭 줄임

![[Pasted image 20240115233121.png]]

- 오토인코더를 통해서 Perceptual Compression 을 진행한 뒤, Semantic Compression 을 Diffusion 이 학습

![[Pasted image 20240115233226.png]]

# Architecture
---
- 트랜스포머의 텍스트 인코더 블럭 사용, U-Net 에 Cross Attention 추가하여 Condition 주입
-  Stable Diffusion은 텍스트 인코더를 CLIP의 텍스트 인코더로 사용

![[Pasted image 20240115233246.png]]


# Training
---
- 학습된 autoencoder를 사용하여, 이미지에 대한 latent representation 획득
- Latent representation을 이용하여 Diffusion Model을 학습

![[Pasted image 20240115233641.png]]