# Series
Series란 pandas에서 사용하는 일종의 리스트
```python
import pandas as pd
```
## 1. 시리즈 만들기
1. 딕셔너리로 시리즈 만들기
```python
# 딕셔너리 만들기
dic = {'a':1, 'b':2, 'c':3}
# 시리즈로 변경하기
dic_series = pd.Series(dic)
```

2.  리스트로 시리즈 만들기
```python
# 리스트 만들기
ls = [1,2,3]
# 시리즈로 변경하기
ls_series = pd.Series(ls)
```
### 1.1 인덱스 부여하기 (인덱스 부여하지 않으면 자동으로 0부터 인덱스 부여)
```python
# 시리즈 만들때 인덱스 부여하기
ls_series = pd.Series(ls, index=['a,','b','c'])
```
## 2. 데이터 확인하기
```python
# 시리즈의 값 확인하기
print(dic_series.values)
# 시리즈의 인덱스 확인하기
print(dic_series.index)
# 시리즈의 값의 타입 확인하기
print(dic_series.dtypes)
```