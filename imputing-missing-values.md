# Imputing Missing Values (결측값 대체하기)
결측값 대체 방법인 kNN Imputaion, rpart, mice를 정리했습니다. https://www.r-bloggers.com/imputing-missing-data-with-r-mice-package 에서 prediction 부분을 발췌하여 번역한 내용입니다.
***
## 4. 예측
예측은 결측값을 채우기 위한 가장 세련된 방법이며 knn Imputation, rpart 및 mice와 같은 다양한 접근법이 있습니다.

### 4.1. kNN Imputation
DMwR :: knnImputation은 결측값을 채우기 위해 k-Nearest Neighbors 방식을 사용합니다. kNN imputation은 다음과 같이 간단합니다. 모든 결측치에 대해, 유클리드 거리를 기준으로 'k'개의 근사치를 식별하고, 이 'k'개 관측치의 가중 평균 (거리에 따른 가중치)을 계산합니다.
장점은 함수를 한 번 호출하여 모든 변수의 모든 결측값을 대체할 수 있다는 것입니다. 그것은 전체 데이터 프레임을 인수로 취하며, 어떤 변수를 대체할 지를 지정하지 않아도 됩니다. 그러나 계산 시 반응 변수를 포함하지 않도록 조심하십시오. 왜냐하면 테스트 / 프로덕션 환경에서, 데이터에 결측값이 포함되어 있으면,  (계산 당시에는 알 수 없는) 반응 변수를 사용할 수 없기 때문입니다.

### 4.2 rpart
DMwR :: knnImputation의 한계는 결측값이 팩터 변수에서 나왔을 때 사용하기에 적절하지 않을 수 있다는 것입니다. rpart와 mice는 모두 팩터 변수가 있어도 결측값을 대체할 수 있는 유연성이 있습니다. rpart의 이점은 예측 필드에서 하나의 변수만 0이 아니면 된다는 것입니다.
여기에서 우리는 결측값을 예측하기 위해 kNN대신 rpart를 사용할 것입니다. 팩터 변수를 처리하고 싶으면, rpart 함수를 호출할 때 method=class로 설정합니다. 숫자의 경우 method=anova를 사용합니다. 앞에서 언급한대로, 반응 변수를 train set에 넣지 않아야 합니다.

### 4.3 mice
Multivariate Imputation by Chained Equations의 mice는 결측값 처리를 위한 고급 기능을 제공하는 R 패키지입니다. mice()로 모형을 만들고 complete()로 완성된 데이터를 생성하는 2가지 단계로, 약간은 독특한 방법을 사용합니다. mice(df) 함수는 df 개의 complete 복사본들을 만들어냅니다. 각각의 complete 카피들은 서로 다른 결측값이 대체된 것입니다. complete () 함수는 이러한 데이터 세트 중 하나 또는 여러 개를 반환하며 default는 첫 번째 complete 복사본입니다. 
