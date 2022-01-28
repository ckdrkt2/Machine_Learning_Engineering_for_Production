# Week 2 : Data-centric AI development




## Skewed datasets


![1](https://user-images.githubusercontent.com/72551588/147477283-3fd8be62-74a6-4dc1-84ee-24e9f8bc9952.jpg)

- 데이터 비율이 깨진 데이터 세트를 편향된 데이터 세트라고 합니다.
- 데이터 비율이 편향되어 있는 경우 어떤 모델을 사용해도 높은 정확도를 얻을 수 있습니다.
- 따라서 데이터 비율이 편향되어 있는 경우에는 정확도(accuracy)는 좋은 metric이 아닙니다.
- 이를 해결하기 위해 confusion matrix를 사용합니다.



![image](https://user-images.githubusercontent.com/72551588/147478113-705272ae-337d-4279-aeed-d32bc24502ab.png)
![image](https://user-images.githubusercontent.com/72551588/147478673-0591cac1-38a0-4d76-83d8-66f46809f223.png)

- confusion matrix를 사용하면 precision과 recall을 구할 수 있습니다.
- precision과 recall은 치우친 데이터 세트에 대해서 성능을 평가할 때 정확도보다 더 유용하게 사용할 수 있습니다.
- 만약에 모델이 모두 거짓으로 예측하게 된다면, recall은 0이 되기 때문에 positive examples을 감지할 수 없게 됩니다.


<p align=center><img src="https://user-images.githubusercontent.com/72551588/147478833-a8e2b70b-9df6-4800-8eb3-cb00515e7bea.png"></p>

- 편향된 데이터 세트에 대해 서로 다른 모델을 비교하게 되면 metric으로 precision과 recall을 사용합니다.
- precision과 recall에 차이가 있는 서로 다른 모델을 비교할 때 이를 결합한 F1 score를 사용합니다.
- F1 score는 precision과 recall의 조화평균을 구하기 때문에 둘 중에 더 낮은 점수를 강조합니다.


![image](https://user-images.githubusercontent.com/72551588/147479885-ea9df7bd-6b4b-4c15-bcbb-c48804a2fda2.png)

- F1 score는 다중 클래스 분류에서도 여러 가지 다른 유형의 문제에 대해 얼마나 잘 수행하는지에 대한 평가 메트릭을 제공합니다.
- 또한 각각의 문제에 대한 비교도 가능하기 때문에 이를 활용해 우선순위를 정하는데 활용될 수 있습니다.



## Performance auditing


![image](https://user-images.githubusercontent.com/72551588/147480611-61b6b0f7-f457-418c-8114-f4170f723f0a.png)


fairness/bias 및 다른 가능성있는 문제에 대해 정확성을 위해 시스템을 double check 하는 방법
1. 시스템이 잘못될 수 있는 다양한 방법에 대해서 브레인스토밍을 진행
  - 데이터의 부분 집합에서의 성능
  - 편향된 데이터에 대한 특정 에러
  - 희귀하고 중요한 클래스에 대한 성능
2. 앞서 언급한 문제들에 대한 성능 평가를 위한 메트릭 설정
  - 전체 개발 세트에 대한 성능 평가 대신 데이터 조각에 대한 성능 평가
3. 사업주의 동의 얻기
  - 앞에서 언급한 문제들이 발생할 수 있는 문제들에 대한 가장 합리적인 평가 세트인 것을 알려서 동의를 얻기
  - 문제를 찾으면 downstream 문제를 일으킬 수 있는 시스템을 배포전에 해결하고 업데이트 할 수 있습니다.
  
 
 
![2](https://user-images.githubusercontent.com/72551588/147483015-e49f8a94-614a-428a-b3c2-06e7e98bd4f0.png)

음성 인식 예시
1. 시스템이 잘못될 수 있는 다양한 방법에 대해서 브레인스토밍을 진행
  - 다른 성별과 다른 민족에 대한 정확성 -> 특정 성별과 민족에 대한 편차가 있는 시스템은 문제가 될 수 있음
  - 다른 기기에 대한 정확성 -> 장치마다 마이크 성능이 다름
  - 잘못된 번역이 퍼지는 것에 대한 문제 -> GAN을 갱스터로...
2. 앞서 언급한 문제들에 대한 성능 평가를 위한 메트릭 설정
  - 다른 성별과 주요 악센트를 위한 평균 정확성
  - 다른 기기들의 평균 정확성
  - 공격적인 단어가 퍼지는 것을 확인



## Data-centric AI development



![image](https://user-images.githubusercontent.com/72551588/147484048-eb0eb874-4654-481b-83f3-6c7e22397524.png)

학습 알고리즘의 성능을 개선하기 위한 방법
- 데이터 중심 접근 방식
  - 코드와 모델을 고정하고 반복적으로 데이터를 개선
  - 데이터의 품질을 가장 중요한 요소로 접근
  - 오류 분석 및 데이터 증강(augmentation)를 활용하여 데이터 품질 개선
  
- 모델 중심 접근 방식
  - 데이터를 고정하고 반복적으로 코드 또는 모델을 개선
  - AI에 대한 대부분의 학술 연구는 모델 중심
  

![image](https://user-images.githubusercontent.com/72551588/147484891-61c0659a-1944-4665-9b1f-731728f63e19.png)

- 데이터 증강을 통해 특정 부분의 성능을 개선하면, 가까운 부분도 같이 향상되는 경향이 있다.
- 구조화되지 않은 데이터에 문제의 경우 한 부분의 성능을 개선하면, 인접한 유형의 부분이 많이 향상되고 떨어진 부분은 약간 향상되는 것으로 밝혀졌습니다.
- 따라서 오류 분석을 통해 가장 큰 격차의 위치를 발견하고 이를 개선하는 것이 데이터를 증강하여 성능을 개선하는 것이 가장 효율적인 방법



![image](https://user-images.githubusercontent.com/72551588/147486402-40926224-ecfe-4158-a163-cc2378c0abf9.png)

- 데이터 증강의 목표는 알고리즘은 못하지만 인간이 잘할 수 있는 realistic examples 제작
- 따라서 데이터 증강으로 examples을 생성할 때 HLP가 높고 알고리즘 성능은 낮도록 생성
- 현실적이고 X에서 Y로의 매핑이 명확한 인간이 인식할 수 있고 현재 알고리즘에서 성능이 낮은 데이터를 생성하면 데이터 증강 좋은 성능을 기대할 수 있음


![image](https://user-images.githubusercontent.com/72551588/147487039-8010483d-d7e1-475e-b425-30ea7cd85ba0.png)

- Model iteration은 오류 분석을 사용하여 모델을 반복적으로 교육하고 모델을 개선 방법을 결정하는 것을 의미
- 데이터 중심 접근 방식에서는 오류 분석을 진행하고 데이터를 추가하거나 데이터 품질을 개선하는 것이 더 유용함


![image](https://user-images.githubusercontent.com/72551588/147487784-194566f0-f5f7-4a9f-a9a5-4b3e5e27b978.png)

- 구조화되지 않는 데이터 문제에 대해 작업 중이고 모델이 큰 경우(모델이 충분히 크고 편향이 작은 신경망)
- X에서 Y로의 매핑이 명확한 경우 정확하게 labeled 된 data를 추가해도 정확도가 거의 손상되지 않음
- 모델이 작은 경우 증강된 데이터에 대해 너무 많은 리소스를 사용할 수 있기 때문에 증강되지 않은 다른 데이터에 대해 성능이 저하될 수 있음
<p align=center><img width=60% src="https://user-images.githubusercontent.com/72551588/147488403-b18cc289-1222-4c28-944b-b45bc831d863.png"></p>
- 매핑에 대한 예시


![image](https://user-images.githubusercontent.com/72551588/147488858-2215adc0-29fb-40b0-a065-375858cfe562.png)
![image](https://user-images.githubusercontent.com/72551588/147489813-6f1766b2-6914-4b79-8ec6-3e3e759712b8.png)

- 구조화된 데이터에서는 고정된 사용자와 레스토랑이 너무 많기 때문에 데이터 증강을 하더라도 새로운 사례를 합성하는 방법을 모름
- 따라서 데이터 증강 대신 입력에 대한 features를 추가하는 것이 더 효과적일 수 있음
- 협업 필터링 접근 방식은 사용자 간의 유사성을 파악하여 추천하는 접근 방식
- 콘텐츠 기반 필터링 접근 방식은 콘텐츠의 내용을 보고 추천하는 접근 방식 -> 다른 사람이 좋아하지 않아도 더 좋은 추천을 할 수 있음


![image](https://user-images.githubusercontent.com/72551588/147490064-ecfe0038-3fa2-4ffe-831f-9707776d45a7.png)

- 구조화 되지 않은 데이터의 경우 학습 알고리즘이 features를 자동으로 학습하기 때문에 데이터 증강이 필요
- 하지만 구조화된 데이터 문제의 데이터 반복은 오류 분석을 하고 features를 추가하는 작업을 진행하고 훈련하는 과정을 거치는 것이 효과적


![image](https://user-images.githubusercontent.com/72551588/147490569-13862180-7361-4333-9f7f-e0f365cec755.png)

- 추적해야 할 사항들
  - 알고리즘/코드 버전 추적 -> 이전 실험으로 돌아가서 활용 가능
  - 데이터 세트 추척
  - 하이퍼 파라미터 추적
  - 결과 저장(metric, models)
- 추적 도구
  - 텍스트 파일, (공유)스프레드 시트
  - 실험 추적 시스템(Weight&Biases, Comet, MLflow, Sage Maker Studio)
- 필요한 피쳐들
  - 재현성을 위한 복제 가능한 결과 데이터
  - 요약 메트릭과 심층 분석 -> 특정 실험 결과 이해 도움
  - 리소스 모니터링, 훈련된 모델 시각화, 모델 오류 분석
  

![image](https://user-images.githubusercontent.com/72551588/147491418-bafd9b35-b7f3-4179-b256-7303ee5341c9.png)