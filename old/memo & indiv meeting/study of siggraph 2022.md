## SIGGRAPH 2022



1. **Shape Analysis and Approximation**

   1. Xu, Xianghao, et al. "Unsupervised Kinematic Motion Detection for Part-segmented 3D Shape Collections." *ACM SIGGRAPH 2022 Conference Proceedings*. 2022.
      1. articulated object에 대한 motion annotations을 찾는 모델
      2. self-supervise with category closure: all valid articulations of category C is C -> C
      3. alternating optimization scheme
      4. latent 상에서 가까운 joint들을 구하고 translation & rotation & some transforms for bias만으로 변환, recon error와 다양한 패널티들로 최적화

   1. Gao, Xifeng, Kui Wu, and Zherong Pan. "Low-poly mesh generation for building models." *ACM SIGGRAPH 2022 Conference Proceedings*. 2022.
      1. 정교한 3D 모델을 만들고 최적화를 위해 low-poly ver. 만드는 것을 자동화
      2. Visual Hull을 만들고 iterative하게 carving하여 개선하는 방법

2. **Volumes and Materials**
   1. Fan, Jiahui, et al. "Neural BRDFs: Representation and Operations." *arXiv preprint arXiv:2111.03797* (2021).
      1. 현실적인 표현을 위한 정교한 BRDFs(e.g. SVBRDFs)는 용량 및 계산이 비싸고, 유연하지 못함
      2. 최신 연구 분야인 neural BRDF는 compression & query에만 집중한다
      3. latent 상에서 importance sampling(for 모던 렌더링 최적화), mixing/interpolating(for generating new, texture mapping per spatial loc., layering to represent coating or etc.)을 가능케 하자
      4. latent 상에서의 BRDF operation을 위한 네트워크는 따로 학습
      5. 압축과 generic operation을 하는 두 네트워크는 블랙박스 BRDF 대수를 구성
      6. 각 텍셀이 latent를 갖도록 텍스쳐를 만들어 렌더링하면 유연하지만 MC보다 빠름
   2. Hu, Yiwei, et al. "Node Graph Optimization Using Differentiable Proxies." *ACM SIGGRAPH 2022 Conference Proceedings*. 2022.
      1. Graph-based Procedural Material, 그래프 모델을 만들고 파라미터 튜닝은 힘듬
      2. Differentiable function만으로 그래프를 만든다면 단순 gradient로 최적화 가능
      3. StyleGAN2같은 differentiable neural net으로 differential proxy를 만들어 최적화하자

3. **Neural Objects, Materials and Illumination**
   1. Cheng, Ziang, et al. "Diffeomorphic Neural Surface Parameterization for 3D and Reflectance Acquisition." *ACM SIGGRAPH 2022 Conference Proceedings*. 2022.
      1. 여러 장의 correspondence-free(e.g. illumination)한 사진으로부터 shape & svBRDF
      2. shape 네트워크와 BRDF 네트워크 각각을 두고 물리 기반 이미지 모델로 합쳐 gradient로 최적화
      3. smooth 3D velocity field로 shape를 표현(velocity field는 diffeomorpism & orientation-preserving이기 때문), 구를 찌그러뜨려서 shape을 만든다
      4. shape는 recurrent Resnet, svBRDF는 MLP
   2. Datta, Sayantan, et al. "Neural Shadow Mapping." *ACM SIGGRAPH 2022 Conference Proceedings*. 2022.
      1. 인풋 screen-space buffer, 아웃풋 raytracing shadow로 학습
      2. 최대한 간단하게 유지하고 최적화 기법을 더해 가볍고 확장성 있게 함
      3. 속도가 중요해서 feature selection을 쓰지 않고 직접 분석해서 사용, relative sensitivity로 분석하는데 성능은 좋지만 robust하지 못하고 너무 작위적이지 않은지?
      4. VGG perceptual loss는 aliasing and sharper etc. 향상, historical buffer 대신 noise-to-noise 채택해서 temporal stability를 얻음
   3. Kuznetsov, Alexandr, et al. "Rendering Neural Materials on Curved Surfaces." *ACM SIGGRAPH 2022 Conference Proceedings*. 2022.

4. **Image/Video Editing and Generation**
   1. Zhang, Yuxin, et al. "Domain enhanced arbitrary image style transfer via contrastive learning." *ACM SIGGRAPH 2022 Conference Proceedings*. 2022.
   2. 