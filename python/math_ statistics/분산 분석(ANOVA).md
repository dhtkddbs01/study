# 분산분석(ANOVA)
- 3개 이상의 다수 집단을 비교할 때 사용하는 검정 방법
- F분포 사용 ( F = 집단 간 분산 / 집단 내 분산)

### 등분산성 가정
- 집단 내 분산이 서로 비슷한가? 비슷해야 비교 가능하다.

### 검정 순서
- 1\. Ommibus F 검정
  - F값이 큰가? 차이가 있는가?
- 2\. post hoc 검정 (검정후 차이=상관관계 분석)
  - 구체적으로 얼마나 차이가 나는가?
    
>
```python
import pandas as pd
import seaborn as sns
import scipy.stats as stats
import matplotlib.pyplot as plt
from scipy.stats import shapiro
from scipy.stats import levene
from sklearn.datasets import load_iris
from statsmodels.stats.multicomp import pairwise_tukeyhsd
# 데이터 불러오기
iris = load_iris()
# 불러온 데이터를 데이터 프레임으로 변환하기
iris_df = pd.DataFrame(data=iris.data, columns=iris.feature_names)
# 타겟데이터를 데이터프레임으로 만들기
target_df = pd.DataFrame(data=iris.target, columns=['target'])
# 타겟데이터와 표본데이터를 합치기
df = pd.concat([iris_df, target_df], axis=1)
# 데이터 열 이름 바꾸기
df.columns = ['sepal_length', 'sepal_width', 'petal_length', 'petal_width', 'target']
sns.boxplot(x='target', y='sepal_width', data=df)
plt.show()
```

### 정규성 검정
- 귀무가설 : 정규분포를 따른다.
- 대립가설 : 정규분포를 따르지 않는다.

>
```python
# 정규성 검정(pvalue가 0.05보다커야 정규분포를 따른다)
print(shapiro(df.sepal_width[df.target==0]))
print(shapiro(df.sepal_width[df.target==1]))
print(shapiro(df.sepal_width[df.target==2]))
# 결과: ShapiroResult(statistic=0.97171950340271, pvalue=0.2715264856815338)
# 결과: ShapiroResult(statistic=0.9741330742835999, pvalue=0.33798879384994507)
# 결과: ShapiroResult(statistic=0.9673910140991211, pvalue=0.1809043288230896)
```
검정결과 세가지 다 pvalue가 유의수준보다 높으므로 귀무가설을 기각하고 정규분포를 따르지 않는다는 대립가설을 채택한다.

#### 등분산성 검정
- 귀무가설 : 등분산성을 만족한다
- 대립가설 : 등분산성을 만족하지 않는다.(이분산이다)

>
```python
# 등분산성 검정
print(levene(df.sepal_width[df.target==0],
             df.sepal_width[df.target==1],
             df.sepal_width[df.target==2]))
# 결과: LeveneResult(statistic=0.5902115655853319, pvalue=0.5555178984739075)
``` 
검정결과 pvalue가 유의수준보다 높으므로 귀무가설을 기각하고 등분산성을 만족하지 않는다는 대립가설을 채택한다.

## 일원 분산분석 (one-way ANOVA)
- 귀무가설 : 집단(target) 간의 sepal_width 차이가 없다.
- 대립가설 : 집단(target) 간의 sepal_width 차이가 있다.

>
```python
# 일원 분산분석
stats.f_oneway(df.sepal_width[df.target==0], df.sepal_width[df.target==1], df.sepal_width[df.target==2])
# 결과 : F_onewayResult(statistic=49.160040089612075, pvalue=4.492017133309115e-17)
```
분석결과 pvalue가 유의수준(0.05)보다 큼으로 귀무가설 기각, 대립가설 채택 => 집단(target)간의 sepal_width차이가 있다.

### 사후분석 (Post-Hoc)
- 구체적으로 어떤 차이가 나는지 검증하는 방법
- Family Wise Eroor Rate
    - 하나의 가설에서 1종 오류가 발생할 가능성
    - 가설 검정을 많이 할 수록 FWER은 증가

>
```python
# 사후분석
hsd = pairwise_tukeyhsd(df['sepal_width'], df['target'], alpha=0.05)
hsd.summary()
```
Multiple Comparison of Means - Tukey HSD,  
					FWER=0.05
group1	group2	meandiff	p-adj	lower	upper	reject
0		1		-0.658		0.001	-0.8189	-0.4971	True
0		2		-0.454		0.001	-0.6149	-0.2931	True
1		2		0.204		0.0088	0.0431 	0.3649	True

