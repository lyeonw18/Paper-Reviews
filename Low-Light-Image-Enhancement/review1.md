# Paper Review 1

## Paper Info
- Title: Deep Retinex Decomposition for Low-Light Enhancement
- Authors: [Chen Wei]
- Conference/Year: 2018
- Link: [논문 링크](https://arxiv.org/abs/1808.04560)

## Summary
저조도 이미지 개선을 위한 딥 러닝 기반의 Retinex-Net 모델을 제안

### Background
- 전통적인 Retinex 모델은 이미지를 반사율(reflectance)과 조명(illumination)으로 분해하여 저조도 문제를 해결
- 기존 방식들은 다양한 장면에서 한계가 있는 수작업 제약 조건 사용

### Approach
- 저조도/일반 조도 이미지 쌍으로 구성된 LOL(LOw-Light) 데이터셋 구축
- Decom-Net(분해 네트워크)과 Enhance-Net(조명 조정 네트워크)을 포함하는 Retinex-Net 개발
- Decom-Net: 쌍을 이루는 이미지들이 일관된 반사율을 공유해야 한다는 제약 조건 적용
- 조명의 구조 인식 평활도 제약 조건 사용 → 지도 학습 없이 분해 학습
- 종단 간(end-to-end) 학습 가능한 프레임워크

### Features
1. **과노출 방지 및 적절한 밝기 조정**  
   - 학습 기반의 이미지 분해와 멀티 스케일 조도 맵 조정으로 어둠 속 객체를 과노출 없이 충분히 밝게 만듬

2. **구조 보존 및 어두운 경계 제거**  
   - 조도 맵의 부드러움을 유도하면서 반사율 그레디언트 가중치 TV 손실(weighted TV loss) 사용 → 어두운 경계선 발생 방지

3. **분해 결과의 우수성**  
   - 저조도 이미지 반사율은 일반 조도 이미지 반사율과 매우 유사

4. **공동 저조도 개선 및 잡음 제거**  
   - 조도 개선 과정에서 증폭될 수 있는 잡음을 반사율 맵에 대해 별도 denoising 적용 → 공동 잡음 제거  
   - LIME, JED와 비교 시 디테일 보존 우수

### Conclusion
- Retinex-Net은 학습 기반 분해를 통해 기존 방법의 한계를 극복  
- 과노출 없이 자연스러운 밝기 조정과 구조 보존  
- 저조도 이미지 개선 성능 우수
