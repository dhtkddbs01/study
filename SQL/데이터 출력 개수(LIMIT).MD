# LIMIT
동물 보호소에 가장 먼저 들어온 동물의 이름을 조회하는 SQL 문
- LIMIT => 출력할 ROW 개수 선택
```SQL
SELECT NAME
FROM ANIMAL_INS
ORDER BY DATETIME
LIMIT 1;
```