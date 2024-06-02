# GROUP BY
- 그룹 외부에서 묶어 순위 및 그룹별 집계를 구할 때 사용
- 특정 원하는 컬럼에 대해서 추출해 결과값 보여줌
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

# PARTITION BY
- 그룹 내 순위 및 그룹별 집계를 구할 때 사용
- 전체 데이터에서 원하는 결과값 보여줌
```SQL
SELECT Continent
	   ,SUM(GNP) OVER(PARTITION BY Continent)
FROM world.country;


SELECT Name
	   ,Continent
       ,Region
       ,max(SurfaceArea) over(PARTITION BY Region)
FROM world.country;
```