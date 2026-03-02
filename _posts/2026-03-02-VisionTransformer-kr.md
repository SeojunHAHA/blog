---
title: "[ViT] An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale"
tags:
  - Computer Vision
categories:
  - Paper
lang: ko
sidebar:
  nav: docs-kr
aside:
  toc: true
---

## Introduction
# 문제 제기

오늘 리뷰해 볼 논문은 An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale 입니다.
NLP에 활용하기 위해 고안된 Transformer 구조를 이미지 분류에 적용시켜 SOTA급 성능을 달성했던 Vision Transformer 모델 논문입니다

이전까지 큰 스케일의 이미지 작업은 ResNet과 같이 CNN 계열의 모델이 최고 수준의 성능을 보여왔었습니다. 그러나, NLP에서 Transformer 구조가 성능을 혁신하며 SOTA를 갱신한 것 처럼, 이 구조를 최소한의 변화만으로 이미지 분류 문제에도 적용시켜 좋은 성능을 이끌어 낼 수 있는지에 대한 논문입니다.

# 목표
![]({{ site.baseurl }}/assets/images/posts/VisionTransformer/1.jpg)
Transformer의 구조는 CNN 모델이 기본적으로 갖고있는 전제인 Inductive bias가 부족하다고 언급합니다. 

Inductive biases:
1. Equivariance(불변성)
- 사물이 이미지 내에서 어느 위치에 있든 동일한 특징으로 인식하는 능력
2. Locality(지역성)
- 이미지의 특정 픽셀은 주변 픽셀들과 밀접한 관련이 있다는 가정

그러나 필자는 모델이 더 큰 데이터셋으로 학습 하였을 때, 이 문제 극복 가능하다고 합니다. 따라서 ViT(Vision Transformer)는 충분히 큰 데이터셋에서 Pre-trained 된 모델을 작은 dataset으로 전이학습(Transfer learning) 시켰을때 좋은 성능을 보였습니다.
    
현재까지 Transformer 구조가 Computer Vision에 적용되어온 사례들은 있었지만, CNN과 Transformer 결합, 혹은 모든 픽셀에 대해 Attention 매커니즘을 사용해 연산량이 너무나 크다거나, 순수 Transformer 구조를 사용했던 연구는 Large-scale의 데이터셋에 대한 학습을 진행하지 않았다는 점입니다.