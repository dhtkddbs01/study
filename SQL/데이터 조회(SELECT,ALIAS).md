# SELECT
`select 컬럼명 from 테이블명 where 조건절`
- 실행 순서
  - from => where => group by => having => order by => select
```sql
-- melon_chart의 모든 컬럼 선택
select * from melon_chart;
```

## limit
```sql
-- melon_chart 테이블의 무작위 데이터 3개 출력
select * from melon_chart limit 3;
```

## distinct
```sql
-- melon_chart 테이블의 singer테이블 중복없이 선택
select distinct singer from melon_chart;
```

## count
```sql
-- melon_chart 테이블의 singer테이블 중복없이 카운트
select count(distinct singer) from melon_chart;

-- melon_chart 테이블의 singer테이블 중복없이 카운트하고 cnt로 헤더 설정
select count(distinct singer) as cnt from melon_chart;
```

## 조건절
```sql
-- melon_chart테이블에서 조건절에 해당하는 데이터 출력
select * from melon_chart where singer = 'NewJeans' and ranking < 6;
```