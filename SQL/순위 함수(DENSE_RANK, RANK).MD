# DENSE_RANK
- 파티션 내 현재 행의 순위를 반환한다. 동점인 경우 동일한 순위를 반환한다. 공동 순위가 존재 해도 다음 순위는 **연속된 값으로 이어진다**. (예시: 1, 2, 2, 3, ……)

```sql
SELECT id, amount, DENSE_RANK() OVER(ORDER BY Population DESC) AS rnk
FROM DATA
```

# RANK
- 파티션 내 현재 행의 순위를 반환한다. 동점인 경우 동일한 순위를 반환한다. 공동 순위가 존재하는 경우, 다음 순위는 그 수만큼 **건너뛰어 매겨진다**. (예시: 1, 2, 2, 4, ……)

```sql
SELECT RANK() OVER(ORDER BY Population DESC) AS rnk
FROM DATA
```