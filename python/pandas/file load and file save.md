# 파일 불러오기
```python
import pandas as pd
```
## 1. csv 파일
### 1.1 불러오기
- index_col : 인덱스로 사용할 컬럼
- usecols : 사용할 컬럼
```python
# 저장되어 있는 경로 복붙하기
csv_file_path = '경로/파일명.csv'
# PassengerId를 인덱스로 사용, ['PassengerId','Survived','Pclass','Age'] 컬럼들을 사용
csv_data1 = pd.read_csv(csv_file_path, index_col = 'PassengerId', usecols = ['PassengerId','Survived','Pclass','Age'])
```

### 1.2 저장하기
```python
# 저장할 공간 경로 붙여넣기
csv_file_path1 = '저장 경로/파일명.csv'
csv_data1.to_csv(csv_file_path1)
```
## 2. excel 파일
### 2.1 불러오기
- sheet_name : 불러올 시트 이름
- header : 컬럼 이름으로 사용할 행
- index_col : 인덱스로 사용할 컬럼
- usecols : 사용할 컬럼
```python
# 저장되어 있는 경로 복붙하기
excel_file_path = '경로/파일명.xlsx'
# '시트1' 시트를 불러옴, 1번째 행을 컬럼 이름으로 사용, PassengerId를 인덱스로 사용, ['PassengerId','Survived','Pclass','Age'] 컬럼들을 사용
excel_data1 = pd.read_excel(excel_file_path, sheet_name='시트1', header=1, index_col = 'PassengerId', usecols = ['PassengerId','Survived','Pclass','Age'])
```


### 2.2 저장하기
```python
# 저장할 경로와 저장할 이름 지정
excel_file_path1 = '저장할 경로/파일이름.xlsx'
# 저장할 시트 지정
excel_data1.to_excel(excel_file_path1, sheet_name = 'sheet1')
```
## 3. html 파일
### 3.1 불러오기
- `pd.read_html(html경로)`
- `encoding`: 한글이 깨져서 나올 때 \`utf-8/cp949\`로 설정
```python
# html 경로 복붙하기
html_path = 'https://finance.naver.com/sise/sise_quant.naver'
# 한글이 깨져서 나올경우 cp949입력
html_data = pd.read_html(html_path, encoding='cp949')
```