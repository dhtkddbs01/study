# GROUP BY
```sql

-- animal_info 테이블에서 animal 별로 데이터를 그룹핑하고 갯수 파악 
select animal, count(*) from animal_info group by animal;

-- animal_info 테이블에서 animal 별로 평균 나이와 나이 합계 출력 
select animal, sum(age), avg(age) from animal_info group by animal;

-- animal_info 테이블에서 age 별로 나이 분포 출력 
select age, count(*) from animal_info group by animal;

-- animal_info 테이블에서 animal별로, 종족 별로 데이터를 그룹핑하고 갯수 파악 
select animal, type, count(*) from animal_info group by animal, type order by animal;
```