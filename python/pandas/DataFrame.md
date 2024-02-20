# DataFrame
Series를 이어붙여 표 형태로 만든 구조
```python
import pandas as pd
```

## 1. 데이터 프레임 만들기
### 1.1. 딕셔너리로 데이터 프레임 만들기
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
### 1.2. 리스트로 데이터프레임 만들기
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
### 1.1. 시리즈를 결합해서 데이터프레임 만들기

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

### 2.1. 상위 행, 하위 행 확인하기
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

### 2.2. 데이터프레임 정보 요약하기
```python
# 전체 행의 갯수, 컬럼 정보, 결측치, 데이터 타입 보여주기
data.info()
# 컬럼별 값의 갯수, 평균, 표준편차, 최솟값, 최댓값, 사분위수를 보여주기
data.describe()
```

## 3. 데이터 추출하기
### 3.1. loc
레이블 값을 사용하여 조회
- 열만 조회할때는 행 조건에 ':'를 입력
  
```python
# 3번째 행의 모든 데이터 출력
df.loc[3,]
# Name 컬럼에 해당하는 데이터 출력
df.loc[:,'Name']
# 3~5번재 행의 데이터와 Age와 Pclass 열의 데이터 출력
df.loc[3:5,['Age','Pclass']]
```

### 3.2. iloc
위치인덱스를 사용하여 조회
- `데이터프레임명.iloc[행인덱스조건,열인덱스조건]`

```python
# [3:5] 인덱스에 해당하는 행의 데이터 출력
df1.iloc[3:5,]
# 1,3,5 인덱스에 해당하는 행의 데이터 출력
df1.iloc[[1,3,5],]
```

### 3.3. 조건을 충족하는 데이터 추출하기
```python
# 데이터프레임명[조건식]
df[df['Pclass'] == 1]
df[(df['Pclass'] == 1) & (df['Age'] >= 30)]
# 데이터프레임명.query('조건식')
df.query('Pclass == 1')
df.query('Pclass == 1 and Age >= 30')
```
## 4. 데이터프레임 수정하기
### 4.1. 인덱스
#### 4.1.1. 열을 인덱스로 변환
##### 4.1.1.1. set_index()
```python
# Name열을 인덱스로 설정
df1 = df.set_index('Name')
```
#### 4.1.2. 인덱스 변경
##### 4.1.2.1 rename()
- 인덱스 몇 개를 바꿀 때
```python
# 데이터명.rename({인덱스:바꿀 인덱스, 인덱스:바꿀 인덱스, ...})
df1.rename({0:'row1', 1:'row2'})
```
##### 4.1.2.2. index()
- 인덱스 전체를 바꿀 때
```python
# 데이터명.index = 바꿀 인덱스 리스트
df1.index = [i+1 for i in range(len(df1))]
```
#### 4.1.3. 인덱스를 열로 변환
##### 4.1.3.1. reset_index()
```python
# 인덱스를 열로 변환하고 그 열을 남기기
df1.reset_index()
# 인덱스를 열로 변환하고 그 열을 삭제하고 싶으면 drop=True
df1.reset_index(drop=True)
```

### 4.2. 데이터 정렬
##### 4.2.1. sort_values
```python
# 'Age'컬럼 기준으로 오름차순 정렬
df.sort_values('Age')
# 'Age'컬럼 기준으로 내림차순 정렬
df.sort_values('Age', ascending=False)
```
### 4.3. 행
#### 4.3.1. 행의 추가/제거
##### 4.3.1.1. concat()
- 행의 추가(병합)
```python
# pd.concat([기존 데이터명, 붙일 데이터명])
df3 = pd.concat([df1, df2])
```
###### 4.3.1.2. drop()
- 행의 제거
```python
# df3.drop([인덱스명, axis=0])
df3.drop([1,2,3,4])
```
#### 4.3.2. 행 중복 제거
##### 4.3.2.1. drop_duplicates()
```python
# 데이터명.drop_duplicates()
df3.drop_duplicates()
```

### 4.4. 열
#### 4.4.1. 열의 추가/제거
- 열의 추가
```python
# 데이터명[추가할 컬럼명] = 추가할 값
df1['age_simplified'] = df1['Age']//10 * 10
```
- 열 제거
```python
# 데이터명.drop(제거할 컬럼명, axis=1)
df1.drop('given_name', axis=1)
```
#### 4.4.2. 열 이름 변경
##### 4.4.2.1. rename()
- 열 이름 하나를 바꿀 때
```python
# 데이터명.rename({열이름:바꿀이름, 열이름:바꿀이름, ...}, axis=1)
df1.rename({'PassengerId':'Id'}, axis=1)
```
##### 4.4.2.2. columns()
- 열 이름 전체를 바꿀 때
```python
# 데이터명.columns = 열 이름 리스트
df1.columns = [i for i in range(12)]
```