# Z-score 표준화

```python
from sklearn.preprocessing import StandardScaler

# Time 열 분리
datetime_column = df['Time']
df = df.drop(columns=['Time'])

# StandardScaler 객체 생성
scaler = StandardScaler()

# 데이터 표준화
scaled_data = scaler.fit_transform(df)

# 표준화된 데이터를 데이터프레임으로 변환
df_scaled = pd.DataFrame(scaled_data, columns=df.columns)

# Time 열과 표준화된 데이터 합치기
df_scaled.insert(0, 'Time', datetime_column)
 
print("Original Data:")
print(df)
print("\nStandardized Data:")
print(df_scaled)
```