# cohort 차트
## 데이터 전처리
```python
# 'order_date'와 '가입연월'에서 연월 정보만 추출하여 새로운 컬럼 생성
df['order_month'] = df['order_date'].dt.to_period('M')
df['가입연월'] = df['가입연월'].dt.to_period('M')

# 2021년 이후에 가입한 고객들의 데이터만 필터링
df_filtered = df[df['가입연월'] >= '2021-01']

# 고객이 첫 구매를 한 월('가입연월')과 구매한 월(order_month)의 차이(기간)를 계산하여 재구매 기간 컬럼 생성
def cohort_index(df):
    df['재구매기간'] = ((df['order_month'] - df['가입연월']).apply(lambda x: x.n)) + 1
    return df

df_filtered = df_filtered.groupby('customer_no').apply(cohort_index)
```
![alt text](python\sklearn\이미지\image-1.png)
```python
# 코호트별 사용자 수 계산
cohort_data = df_filtered.groupby(['가입연월', '재구매기간']).agg(n_customers=('customer_no', 'nunique')).reset_index()
```
![alt text](python\sklearn\이미지\image-2.png)
```python
# 코호트별 첫 달 사용자 수로 나누어 retention 계산
cohort_counts = cohort_data.pivot(index='가입연월', columns='재구매기간', values='n_customers')
base = cohort_counts[1]
retention = cohort_counts.divide(base, axis=0).round(3)
```
![alt text](python\sklearn\이미지\image-3.png)
## 시각화
```python
# 코호트 차트 그리기
plt.figure(figsize=(12, 8))
sns.heatmap(retention, annot=True, fmt='.0%', cmap='Blues')
plt.title('총 고객 cohort')
plt.ylabel('가입연월')
plt.xlabel('개월')
plt.show()
```
![alt text](python\sklearn\이미지\image.png)