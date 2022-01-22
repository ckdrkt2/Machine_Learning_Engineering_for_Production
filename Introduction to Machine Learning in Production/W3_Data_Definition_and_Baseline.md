# Week 3 : Data Definition and Baseline




## Define Data and Establish Baseline


Why is data definition hard???

<img src="https://user-images.githubusercontent.com/72551588/147566157-bc6e117b-0b62-48df-b947-e8e08ab5c21b.png" width=49%> <img src="https://user-images.githubusercontent.com/72551588/147568401-1946df28-caae-44a0-9476-c34b5d580442.png" width=49%>

- 일정한 지정 규칙에 의해(한 명의 라벨러에 의해) 레이블을 지정하면 성능을 낼 수 있지만,
- 각 다른 레이블 지정 규칙으로 된 데이터 세트를 사용하면 학습 알고리즘에 악영향을 줌
- 따라서 레이블 지정에 선호도나 규칙에 따라 성능이 차이가 발생할 수 있지만 일관성이 유지되지 않은 레이블 지정을 피해야 함



![image](https://user-images.githubusercontent.com/72551588/147569833-30ced27b-bdaa-4f60-b425-0a76aa529e44.png)

- 데이터 레이블 규칙을 표준화하는 것을 통해 알고리즘 인식 성능에 도움이 될 수 있음
- 예시와 같이 모호한 경우에는 명시적으로 두 계정을 연결한 데이터가 있다면 알고리즘 훈련에 레이블 지정이 좋은 데이터 세트가 될 수 있음
- 하지만 모호한 데이터의 경우 이를 레이블 할 수 있는 추가적인 수단이 필요함 -> 일반적으로는 일관된 레이블 지정


![image](https://user-images.githubusercontent.com/72551588/147570623-57daf7f8-f16a-455d-9d82-b5f304021928.png)

- 따라서 좋은 성능을 위해서는 모호한 데이터의 경우(사람도 구분하기 어려운 경우) 데이터의 품질을 향상시키는 것이 더 좋은 레이블 지정을 도움
- 앞의 데이터 병합 예시에서도 추가적인 데이터를 활용하여 성능을 개선할 수 있음


![image](https://user-images.githubusercontent.com/72551588/147571153-1f481c4e-ce03-4e04-854d-cd8347c9fd05.png)

- 대부분의 Unstructured data 문제의 경우에 인간이 데이터 추가 및 증강에 도움을 줄 수 있음
- Structured data 문제의 경우에는 데이터 추가 및 증강이 어려움 -> 인간이 도움을 줄 수는 있지만 한계가 있음
- 데이터 세트의 크기가 작은 경우 clean labels이 중요함 -> 레이블 지정이 일관성 있는지
- 데이터 세트의 크기가 큰 경우 수동으로 데이터 처리는 불가능 -> clean labels가 중요하지만 데이터 처리에 한계가 있기 때문에 데이터 프로세스 중심으로 함


![image](https://user-images.githubusercontent.com/72551588/147573658-6ac7fe27-62e0-4c30-b130-48aad1038f82.png)

- 노이즈가 많은 데이터는 예측이 어려움 -> Big data를 통해 어느 정도 정확한 예측은 가능
- 하지만 일관성 있게 레이블이 지정된 작은 데이터의 경우 많은 데이터가 없어도 정확한 예측이 가능
- 결과적으로 데이터를 추가하는 것 보다 레이블 지정 규칙을 일관되게(표준화) 바꾸는 것이 중요

![image](https://user-images.githubusercontent.com/72551588/147574257-0bc20f8f-859a-4366-81f0-341c3df5e133.png)

- Big data 문제들은 small data의 문제들을 가지고 있을 수 있음
- 따라서 많은 데이터를 수집하고 증강해도 희귀한 이벤트에 대해 일관된 레이블을 지정하는 것도 중요함


![image](https://user-images.githubusercontent.com/72551588/147574534-3aa18fe5-5c7d-4790-8127-506a5541ff02.png)

레이블 지정 일관성을 향상시키는 방법
- 예시를 통해 동일한 레이블 지정 유도
- 일관된 합의가 나올때까지 라벨러와 머신러닝 엔지니어 논의 진행
- 입력 X에 충분한 정보가 없다고 판단될 경우 입력 X를 변경 -> 데이터 레이블 지정이 어려울 때 데이터 개선
- 위 과정을 반복적으로 진행


![image](https://user-images.githubusercontent.com/72551588/147576004-1c4d6ba9-c4e8-455a-8fc0-70b16794e568.png)

- 또 다른 방법은 레이블 지정에 모호함이 있을 때 이를 인정하고 새로운 클래스를 만들어서 분류하는 것
- 이를 통해 레이블 지정을 더 일관되게 할 수 있음


![image](https://user-images.githubusercontent.com/72551588/147576220-a08abb81-bebe-4d82-a80d-56a085fb7680.png)



### Why measure HLP?

- 가능성 범위에 대해 기준서을 설정하는데 유용함
- 추가적으로 Unstructured data 작업의 경우 분석 및 우선 쉰위 지정을 도와줌
- (+) 학계에서는 인정가능한 벤치마크로 사용됨
- (+) 비즈니스에서 비현실적인 목표의 경우 HLP로 목표를 합리적으로 설정함
- (+) 머신러닝 시스템이 인간보다 얼마나 우수한지?


![image](https://user-images.githubusercontent.com/72551588/147577562-9fece213-c5e6-4844-a2c6-01ae313b4a37.png)
- 이해 X...
- 정리하면, HLP를 높이는 것은 레이블의 일관성을 높이기 때문에 더 좋은 결과를 만들 수 있음


![image](https://user-images.githubusercontent.com/72551588/147578021-6517fa2e-a516-4152-a9f0-822c0fe25daf.png)

- 정답 레이블 Y가 사람으로부터 지정된 경우 HLP가 100%보다 꽤 낮은 것은 레이브 지정이 모호하다는 것을 나타냄
- 이 경우 레이블 일관성 향상은 HLP를 끌어올릴 수 있음
- 결과적으로 머신러닝 알고리즘은 일관된 레이블로 인해 HLP를 능가하는 것이 더 어려워짐 -> 이전에 언급된 데이터 향상 규칙


![image](https://user-images.githubusercontent.com/72551588/147578497-83bdf15c-0a9d-4b0a-bcc0-b1dba3c17f99.png)

- HLP는 인간 수준의 성능이 유용한 레퍼런스를 제공할 수 있는 문제에서 중요함


## Label and Organize Data

![image](https://user-images.githubusercontent.com/72551588/147579073-d49726ed-d4b5-4022-b7a0-598fb93adb9e.png)

- 반복적인 수행을 위해 반복 루프을 최대한 빠르게 해야 함
- 데이터 수집 시간은 일정 기간을 정해두고 시작하는 것이 효과적임 -> 창의적인 효과기대
- 단, 이전에 관련된 작업을 수행한 경험이 있을 경우에 -> 어느 정도 시간이 걸리는지와, 어느 정도 이상이 가치가 없다는 것을 알기 때문에


![image](https://user-images.githubusercontent.com/72551588/147582232-09df2ff2-2859-499d-86aa-3b0ce5a5e4c9.png)

- 데이터를 얻는 다른 효과적인 방법은 데이터 소스 목록을 작성하는 것
- 데이터 소스 목록 작성을 통해 데이터 수집 및 처리에 필요한 소스들을 비교하여 최적의 선택을 할 수 있음


![image](https://user-images.githubusercontent.com/72551588/147582571-407a47a4-a4f1-43a3-a25b-0c579fb61a04.png)

- 데이터 레이블링 지정을 위한 옵션: In-house, outsourced, crowdsourced
- 머신러닝 엔지니어가 데이터 라벨링을 하는 것은 비용이 크지만, 빠른 프로젝트 진행을 위해서는 일반적임
- 음성인식 레이블 지정의 경우 누구나 가능, 전문적인 지식이 필요한 레이블 지정은 전문가가 필요
- 레이블 지정이 어려운 경우 -> 추천 시스템 활용
- 데이터 세트 크기를 10배 이상 늘리는 것은 이후의 일을 예측하는데 어려움이 발생함



<img src="https://user-images.githubusercontent.com/72551588/147584131-0be945a8-874c-422a-ae28-f41b14573426.png" width=49%>  <img src="https://user-images.githubusercontent.com/72551588/147584134-463c464d-ec33-4b5e-a9b6-bab6f88dcbad.png" width=49%>

- raw data가 주어진 경우 모델에 입력하기 전에 전처리나 데이터 정리를 하는 경우가 있음 -> 모델 배포가 어려워짐
- 이러한 과정에서 재현성(replicability)가 문제가 될 수 있음 -> 여러 strips로 전처리를 진행한 경우

![image](https://user-images.githubusercontent.com/72551588/147584140-6e7475c1-d576-4e3d-a86e-373af3bda9f0.png)

- 그러나 대부분의 프로젝트가 개념 증명 또는 POC 단계에서 app이 실행 가능하고 구축 및 배포할 가치가 있는지 결정하는 단계이기 때문에 실행과 작동에 중점을 둠
- 이후 전처리 재현을 구현 -> 이를 위해 많은 코멘트를 작성하면 좋음 -> 하지만 실행과 작동이 중요한 경우에는 바뀔 수 있음
- Tensorflow Transform, Apache beam, Airflow 등과 같은 정교한 도구를 통해 데이터 파이프라인을 재현



<img src="https://user-images.githubusercontent.com/72551588/147585154-2c5312fc-7597-45f7-9584-c75ebff0eac3.png" width=49%>  <img src="https://user-images.githubusercontent.com/72551588/147585400-a3c25836-fe7e-4247-8af8-b0ac0e220cb7.png" width=49%>
 
- data pipeline에서 모델의 문제 발생, 데이터 세트 업데이트, 데이터 upstream의 일부 변경 등이 발생할 수 있음
- 데이터의 출처를 남겨 추적하는 것은 이러한 상황에 유용함
- Tensorflow Transform과 같은 도구를 사용할 수도 있지만 메타데이터를 활용하는 것을 통해 데이터 파이프라인 관리와 오류 분석, 모델 개발을 쉽게 함
- 메타 데이터를 저장하는 것을 통해 오류 발생 시 발견 확률을 높이거나 데이터의 출처를 추적하는 등 대규모의 복잡한 데이터를 관리하는데 효과적



![image](https://user-images.githubusercontent.com/72551588/147586020-57520aed-6b04-4864-a4a1-ad6cfa22226b.png)





## Scoping



<p align=center><img src="https://user-images.githubusercontent.com/72551588/147586900-970f629c-ecb6-4c49-9cd6-57f4d4a86c9d.png" width=49%></p>

- scoping은 프로젝트의 리소스와 성공, 평가에 대한 분석을 통해 가장 가치있는 프로젝트를 선택해 영향력을 높이는 것


<img src="https://user-images.githubusercontent.com/72551588/147587558-cf2c5f83-934e-4c09-a1d0-ac7cff8d1ac7.png" width=49%>  <img src="https://user-images.githubusercontent.com/72551588/147587859-151726c8-9dfd-4cd5-998a-12587f289a6d.png" width=49%>

- scoping process
- 비즈니스 문제에 대해 브레인스토밍을 진행 -> 문제를 명확히 하는 것이 도움이 될 수 있음
- AI solutions에 대해 브레인스토밍 -> 이후 solutions의 실현가능성과 가치를 평가
- 방향 결정 후 리소스 예산 편성

★★ 프로젝트를 진행할 때 많은 가능성에 대해 브레인스토밍하는 발산적 사고를 하는 것이 가치가 있을 수 있음 -> 이후 범위를 좁히는 전환 사고를 통해 긍정적 유형의 가치 창출



![image](https://user-images.githubusercontent.com/72551588/147589046-2af8d196-49f4-4c9c-8774-5c1db24c82ed.png)
![image](https://user-images.githubusercontent.com/72551588/147589057-00dc8a17-53b1-4bd6-ae69-bce8ee89a614.png)
![image](https://user-images.githubusercontent.com/72551588/147589065-aa8fb3b8-a904-43fe-b1ee-5d5213c82cb8.png)
![image](https://user-images.githubusercontent.com/72551588/147589069-6420a5a8-2200-44bd-ad1a-49d83ca0e7bf.png)

------------------------------------------------------------------------------------------------------------------------------------------------------------

![image](https://user-images.githubusercontent.com/72551588/147589080-bafeb3a2-174a-447c-b896-513b4b179d0e.png)
![image](https://user-images.githubusercontent.com/72551588/147589095-6129e801-dad8-4d4b-9d2c-907274d5dc49.png)

------------------------------------------------------------------------------------------------------------------------------------------------------------

![image](https://user-images.githubusercontent.com/72551588/147589104-449accec-1630-472b-9876-8e3981bb8a39.png)
