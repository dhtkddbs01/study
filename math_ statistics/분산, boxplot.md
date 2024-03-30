## 분산도
#### 분산, 표준편차
- 자료의 밀집과 퍼짐 정도
- 값이 커질수록 평균이랑 멀어지는 값을 표본을 가짐

>
```python
plt.rcParams['figure.figsize'] = 15,8
plt.figure(figsize=(4,4))
# 분산
import numpy
val = df['사고건수']
var = numpy.var(val)
var
# 표준편차
import math
std = math.sqrt(var)
std
```

## boxplot
### 사분위 범위(IQR)과 이상치의 탐지
#### 사분위수(Quartile)
- 값을 같은 갯수로 4개로 나눈 각각의 값

#### 1사분위수(Q1)
- 25%

#### 2사분위수(Q2)
- Median(중앙값), 50th percentile

#### 3사분위수(Q3)
- 75%

#### 사분위간 범위
- Q3-Q1

#### maximum
- Q3+z.5*IQR

#### minimum
- Q1-1.5*IQR

#### outliers
- minimum보다 작거나
- maximum보다 큰값

>
```python
plt.boxplot(df['사고건수'])
plt.show()
```

![](https://velog.velcdn.com/images/dhtkddbs01/post/d86e864f-129f-46ad-b55b-b6d86ec033d0/image.png)


>
```python
# boxplot 한그림에 두개 그리기
fig, ax= plt.subplots()
ax.boxplot([df['사고건수'], df['중상자수']])
plt.title('2020년 사고건수, 중상자수 Boxplot')
plt.xticks([1,2], ['사고건수', '중상자수'])
plt.show()
```

![](https://velog.velcdn.com/images/dhtkddbs01/post/c8cf69c2-6a44-4aa5-b141-17c5a1a12bef/image.png)

>
```python
# 여러개 boxplot그리기
sns.boxplot(x='시도', y='사고건수', data=df)
plt.show()
```

![](https://velog.velcdn.com/images/dhtkddbs01/post/cb645737-b039-43b7-9752-bcfbb644e77d/image.png)

>
```python
# ym 별 boxplot 그리기
sns.boxplot(x='시도', y='사고건수', hue='ym', data=df)
plt.show()
```

![](https://velog.velcdn.com/images/dhtkddbs01/post/fb42eeb8-9bdf-4279-a794-ad498f801278/image.png)

>
```python
# ym 별 boxplot 따로 그리기
sns.factorplot(x='시도', y='사고건수', col='ym', kind='box', palette='Set3', data=df)
plt.show()
```

![](https://velog.velcdn.com/images/dhtkddbs01/post/78794867-74dc-4eb9-8f86-7c556e61a786/image.png)

