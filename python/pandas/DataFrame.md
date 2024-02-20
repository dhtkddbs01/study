# DataFrame
Series를 이어붙여 표 형태로 만든 구조
```python
import pandas as pd
```

## 1. 데이터 프레임 만들기
1. 딕셔너리로 데이터 프레임 만들기
- 열 단위로 값을 입력할 때 딕셔너리를 이용
- 값의 길이가 모두 같지 않으면 에러가 난다
```python
# 딕셔너리 만들기
dic = {'Name':['John','Merry','Chris']
       , 'Number':[1,2,3]
       , 'Month':['Feb','Oct','Nov']}
# 데이터프레임으로 만들기       
df = pd.DataFrame(dic)
```
2. 리스트로 데이터프레임 만들기
- 행 단위로 값을 입력할 때 리스트를 사용합니다.
- 각 리스트의 길이가 같지 않으면 에러가 납니다.
```python
# 이중 리스트 만들기
ls = [['John', 1, 'Feb']
      ,['Merry',2,'Oct']
      ,['Chris',3,'Nov']]
# 데이터프레임으로 만들기    
df = pd.DataFrame(ls, columns=['Name','Number','Month'])
```
### 1.1 시리즈를 결합해서 데이터프레임 만들기

```python
# 결합할 Series 생성
name_series = pd.Series(['John','Merry','Chris'])
number_series = pd.Series([1,2,3])
month_series = pd.Series(['Feb','Oct','Nov'])
# 결합하기
df = pd.DataFrame({'Name':name_series, 'Number':number_series, 'Month':month_series})
```

## 2. 데이터프레임 확인하기

```python
# 값 확인
print(df.values)
# 인덱스 확인
print(df.index)
# 값의 타입 확인
print(df.dtypes)
# 컬럼명들 확인하기
print(df.columns)
```

### 2.1 상위 행, 하위 행 확인하기
- 지정해주지 않으면 기본으로 5개의 행 조회
```python
# 앞에서 5개
data.head()
# 뒤에서 5개
data.tail()
# 앞에서 10개
data.head(10)
# 뒤에서 10개
data.tail(10)
```

### 2.2 데이터프레임 정보 요약하기
```python
# 전체 행의 갯수, 컬럼 정보, 결측치, 데이터 타입 보여주기
data.info()
# 컬럼별 값의 갯수, 평균, 표준편차, 최솟값, 최댓값, 사분위수를 보여주기
data.describe()
