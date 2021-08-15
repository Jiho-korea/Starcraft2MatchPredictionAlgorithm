# Starcraft2MatchPredictionAlgorithm


![poster](https://user-images.githubusercontent.com/50912180/103545754-5aa25f00-4ee5-11eb-8816-8bbc63003b3f.jpg)


![image](https://user-images.githubusercontent.com/50912180/102563048-ce89ec80-411b-11eb-8e01-95d54366f692.png)


![image](https://user-images.githubusercontent.com/50912180/102901791-60458100-44b1-11eb-8cf2-9ea38437e427.png)

![image](https://user-images.githubusercontent.com/50912180/125723768-a5b15004-75cb-43f6-8a1b-4da8a3dbb3d3.jpg)


# 발표자료 
![슬라이드1](https://user-images.githubusercontent.com/50912180/129496081-4c15b6ed-269f-4a46-9ecd-6196b231fcaf.JPG)
안녕하십니까 포티나이너스팀 발표를 맡은 강지호입니다. 



![슬라이드2](https://user-images.githubusercontent.com/50912180/129496082-f90018ea-34df-44ba-87dc-b5930c56c49f.JPG)
스타 투 승패 예측 정확도를 높여주었던 저희의 데이터 전처리와 알고리즘에 대해 발표하겠습니다. 발표순서는 다음과 같습니다.



![슬라이드3](https://user-images.githubusercontent.com/50912180/129496083-d9d5b358-ef77-41f2-857c-e39a10f49656.JPG)
데이터 전처리에 대해 설명드리겠습니다.



![슬라이드4](https://user-images.githubusercontent.com/50912180/129496084-573428f0-8f5e-4b0b-8255-ececa13a086f.JPG)
전체 데이터 전처리 과정은 원본 데이터에 포함된 이벤트 시간별로 있는 수많은 row들을 한 게임별로 하나의 row로 바꿔주는 것입니다. 



![슬라이드5](https://user-images.githubusercontent.com/50912180/129496087-5370514d-e603-4a25-96b9-ff70a6aea9f0.JPG)
주요 데이터 전처리 솔루션을 크게 Feature 정형화와 EDA솔루션으로 분류 하였습니다!



![슬라이드6](https://user-images.githubusercontent.com/50912180/129496088-0e4d93b2-5822-474c-9d4f-5cf2cfb68df5.JPG)
Feature 정형화는 원본 데이터에 포함 된 가공되지 않은 정보들을 최대한 정형화된 형태로 만드는 Feature Engineering입니다. Feature 정형화의 1,2,3번은 비슷한 내용이어서 1번만 설명드리겠습니다



![슬라이드7](https://user-images.githubusercontent.com/50912180/129496059-f6edb491-8922-48e8-b780-104312d2fe7c.JPG)
첫번째 Feature 정형화입니다.
원본데이터에서 Event칼럼의 값이 Ability일 떄 event_contents칼럼의 내용은 
사진과 같이 16진수의 코드와 매핑되는 상세내용으로 구성됩니다. 저희는 플레이어 별로 같은 코드가 몇번 나오는지, count 값을 전부 칼럼으로 만들어 줬습니다.



![슬라이드8](https://user-images.githubusercontent.com/50912180/129496062-9d4c805a-f9e4-499f-8cc8-ee9c5c11e734.JPG)
두번째 Feature 정형화입니다.
코드가 5A0이면 공격을 의미하고 우측 상세내용은 공격 대상을 의미하는 데요
플레이어의 공격대상별 공격횟수는 승패에 영향을 미쳐서 모두 칼럼으로 만들어 주었습니다.



![슬라이드9](https://user-images.githubusercontent.com/50912180/129496064-2a03e3c0-bade-42bf-8d9a-806faae88f0d.JPG)
다음은 EDA 를 통한 Feature Engineering입니다. 1번 솔루션부터 설명드리겠습니다.



![슬라이드10](https://user-images.githubusercontent.com/50912180/129496065-5ef42798-3789-4bfc-8c44-106656b2c7e4.JPG)
저희는 일꾼 수가 많을 수록 자원채취량이 많아져 승리확률이 높아질거라 생각해 종족별 일꾼에 해당하는 코드의 count값들은 따로 합쳐주었습니다. 그리고 일꾼을 제외한 모든 유닛들의 count값도 따로 합쳐 새로운 칼럼으로 만들어주었습니다.



![슬라이드11](https://user-images.githubusercontent.com/50912180/129496066-dc3f7adc-fb8b-459a-96bd-11ad196385da.JPG)
두번째 솔루션으로 플레이어별 유닛과 건물생산에 소비된 미네랄과 가스의 총량을 구했습니다.



![슬라이드12](https://user-images.githubusercontent.com/50912180/129496067-859cda13-8f13-44dc-932a-894b2817bc2d.JPG)
소비한 미네랄과 가스가 더 많을 수록 전투에서 이길 확률은 높아지기 때문입니다.



![슬라이드13](https://user-images.githubusercontent.com/50912180/129496068-a3917025-4edf-4661-8a12-e4d0e7e9444a.JPG)
유닛과 건물별 생산에 필요한 미네랄과 가스를 미리 딕셔너리로 만들어 주고 이전에 보여드린 코드별 count에 생산 미네랄과 가스를 각각 곱해준 뒤 전부 더하여 구하였습니다. 



![슬라이드14](https://user-images.githubusercontent.com/50912180/129496069-fb460079-f430-42bd-b9fd-b175e5727ae7.JPG)
세번째 솔루션입니다. 저글링이 아무리 많다한들 캐리어 한 기를 절대 죽일 수 없듯이 유닛들의 분류, 그리고 공격 유형에 따라 전투의 유불리가 결정되기 때문에
화면과 같이 총 6종류로 분류해 각 유닛들의 수를 새로운 컬럼으로 만들었습니다



![슬라이드15](https://user-images.githubusercontent.com/50912180/129496070-0a04950d-468b-4a9c-ab1d-671020ab0919.JPG)
사용한 모델과 알고리즘에 대해 설명드리겠습니다.



![슬라이드16](https://user-images.githubusercontent.com/50912180/129496071-c7aa36fc-0809-4d4e-8afb-6db8df9e0852.JPG)
저희 팀은 부스팅 알고리즘의 그레디언트 부스트에 속하는 LGBM알고리즘과 CatBoost알고리즘을 사용하였습니다. 



![슬라이드17](https://user-images.githubusercontent.com/50912180/129496073-ea51813a-6bec-4692-a9f4-c95e49fdf678.JPG)
먼저 앙상블에 대해 설명드리겠습니다. 앙상블이란 여러 개의 Classifier를 생성하고 그 예측을 결합함으로써 보다 정확한 최종예측을 도출하는 기법입니다. 간단하게 집단지성이라 생각하시면 좋습니다.



![슬라이드18](https://user-images.githubusercontent.com/50912180/129496074-6b85fc1a-b18d-4576-a8c1-a68b65305039.JPG)
앙상블에서 좀더 세부적인 부스팅 알고리즘은 여러 개의 약한 학습기를 순차적으로 학습-예측하면서 잘못 예측한 데이터에 가중치 부여를 통해 오류를 개선해 나가면서 학습하는 방식입니다.  이때 오류를 개선하기 위해 경사하강법을 사용하면 그것이 바로 그레이디언트 부스트입니다.




![슬라이드19](https://user-images.githubusercontent.com/50912180/129496075-551bab98-a25d-4d19-8ca7-e49d1e7cbfb1.JPG)
그림으로 설명드리겠습니다. 학습데이터에 이렇게 승과 패가 분포되어 있을 때 첫번째 약한 분류기가 승과 패를 임의의 분류 기준으로 분류합니다. 하지만 이렇게 잘못 예측된 데이터가 있을텐데요. 이런 데이터들에 가중치를 부여합니다. 가중치 부여를 굵은 글씨로 표현했습니다. 그다음, 두번째 약한 분류기는 가중치를 고려하여 새로운 분류기준으로 분류합니다. 이번에도 잘못예측된 데이터에 가중치를 부여하고 다음 약한 예측기는 이 것을 고려하여 또다시 분류합니다. 이 과정을 반복한 후 최종적으로 모든 약한 분류기를 결합하여 보다 승리와 패배를 잘 예측할 수 있도록 하는 것입니다.  



![슬라이드20](https://user-images.githubusercontent.com/50912180/129496076-f1bf4f87-fae8-42e9-ad5c-54bda9973501.JPG)
그렇다면 CatBoost와 LGBM의 차이점은 무엇일까요? CatBoost와 LGBM등 다양한 부스팅 알고리즘은 트리 기반인데요 바로 자식 노드의 생성 방식이 다릅니다.  

CatBoost알고리즘은 트리의 모든 노드에서 자식노드를 생성하는 level-wise알고리즘이지만,
LGBM은 loss가 가장낮은 노드에서 뻗어나가는 leaf-wise 알고리즘입니다.
전자의 경우 과적합에 민감하지 않고 카테고리형 변수의 학습에 좋은 성능을 발휘합니다.
후자의 경우 속도가 빠르고 실행시 적은 메모리를 사용해 큰 사이즈의 데이터를 사용하기 유리합니다.

저희는 이 두 알고리즘을 각각 학습시켜 두개의 모델을 만든 후 각각의 승패 예측 결과를 6:4의 비율로 앙상블하여 예측 성능을 높혔습니다.



![슬라이드21](https://user-images.githubusercontent.com/50912180/129496077-73c28a79-6e49-43e0-a509-7e0481174ebc.JPG)
모델의 주요 하이퍼 파라미터들은 베이지안 최적화를 통해 구하였습니다. 
하이퍼파라미터별로 처음 10회동안 범위 내 랜덤 값으로 score를 계산 해 준 뒤 20회 동안 최적화를 해주었습니다.



![슬라이드22](https://user-images.githubusercontent.com/50912180/129496078-27bf4a95-9eb4-44da-8a05-5890676d25bd.JPG)
모델을 개발할 때 저희가 겪었던 문제점은 저희가 따로 만든 테스트세트의 예측 점수와 public제출점수가 약간 차이가 있었다는 것입니다. 



![슬라이드23](https://user-images.githubusercontent.com/50912180/129496079-e52c2fe6-7e84-473c-937f-cb016ee44791.JPG)
그래서 저희는 기존에 사용하던 LGBM에 CatBoost를 앙상블하고
학습세트에서 0 번, 1번플레이어랑 관련된 모든 칼럼 쌍들의 위치를 뒤바꿔 준 복사본을 원본학습세트에 행병합하는 방식으로 학습세트를 2배로 만든 후, 모델을 학습시켜 문제를 해결했습니다.



![슬라이드24](https://user-images.githubusercontent.com/50912180/129496080-f4aad9bb-c610-494f-8f35-3ee5d97860d1.JPG)
발표를 마치겠습니다. 감사합니다. 

