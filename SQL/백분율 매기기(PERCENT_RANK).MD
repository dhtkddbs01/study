# PERCENT_RANK()
-  백분율 순위를 구할 수 있다.
- 반환 값의 범위는 0에서 1까지이며 아래 수식의 결과로 계산된 행의 상태 순위를 반환
   -  (RANK -1) / (ROWS -1)
- 정렬된 위에서 부터 0~1까지 
```SQL
SELECT PERCENT_RANK() OVER (ORDER BY SIZE_OF_COLONY DESC) AS PERCENT
           , ID
          FROM ECOLI_DATA
```
