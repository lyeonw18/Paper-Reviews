# Paper Review 2

## Paper Info
- Title: EnlightenGAN: Deep Light Enhancement without Paired Supervision
- Authors: [Yifan Jiang ]
- Conference/Year: 2019
- Link: [논문 링크](https://arxiv.org/abs/1906.06972)

## Summary
얻기 어려운 짝지어진(paired) 저조도/일반 조도 이미지 없이 학습할 수 있는 비지도(unsupervised) 생성적 적대 신경망(GAN), EnlightenGAN을 제안

### Background
- 기존 딥러닝 기반 이미지 복원/개선 방법은 손상/깨끗한 이미지 쌍에 의존 (예: 초해상화, 노이즈 제거, 디블러링)
- 저조도 이미지 개선에서는 쌍 데이터 확보가 근본적으로 어렵거나 불가능
- 저조도 조건에서 캡처된 이미지의 문제:
  - 낮은 대비 (low contrast)
  - 떨어지는 가시성 (poor visibility)
  - 높은 ISO 노이즈 (high ISO noise)
- 쌍 데이터 확보의 비실용성:
  - 동시 캡처 어려움 → 실제 장면 저조도/고조도 사진 동시 촬영 불가
  - 합성 이미지 한계 → 충분히 현실적이지 않아 다양한 아티팩트 발생
  - 유일한 정답(Ground Truth) 부재
  - 기존 LOL 데이터셋 제약 → 500쌍 정도만 존재

### Approach
1. 비쌍형(Unpaired) 대규모 데이터 사용
2. Cycle-consistency 없이 원-경로(One-Path) GAN인 EnlightenGAN 프레임워크 개발 → 비지도 학습
3. Generator: 자체 정규화 어텐션 메커니즘이 적용된 U-Net → 입력 이미지 조도 정보 활용, 어두운 영역 집중 개선
4. Global-Local Discriminators 사용 → 과노출/저노출 아티팩트 방지
5. 입력 이미지와 개선된 출력 이미지 간 특징 거리 제한 → 비지도 훈련 정규화
6. 실제 환경 이미지 일반화 능력 향상

### Features
1. **과노출 방지 및 세부 사항 보존**  
   어두운 영역을 밝게 개선하면서 과노출 아티팩트 방지, 텍스처 세부 사항 유지
2. **노이즈 억제 및 가시성 향상**  
   검은 하늘 영역 노이즈 억제, 노출 부족 영역 세부 생성
3. **색상 왜곡 및 불일치 해결**  
   로컬 판별자/어텐션 미적용 버전에서 발생하는 색상 왜곡 완화
4. **정량적/객관적 평가**  
   NIQE 점수에서 낮은 평균 점수 → 높은 시각적 품질
5. **실제 환경 일반화 및 도메인 적응**  
   BBD-100k 데이터셋 적용 시 과노출/노이즈 억제 균형 → 실세계 만족도 높음
6. **고수준 작업 전처리 결과**  
   ExDark 데이터셋 분류 정확도 향상

### Conclusion
- EnlightenGAN은 저조도/일반 조도 이미지 쌍 없이 학습 가능한 효과적 비지도 GAN
- 특징 보존 손실, 어텐션 메커니즘, 전역-지역 판별자 구조로 과노출/저노출 아티팩트 방지
- 주관적/객관적 평가 모두에서 기존 방법 대비 우수, 실세계 일반화 능력 탁월
