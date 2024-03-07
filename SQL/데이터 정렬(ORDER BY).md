# ORDER BY
1. SELECT절 마지막에 작성
2. 기본으로 오른차순 정렬
```sql
-- melon_chart테이블의 모든 데이터를 ranking컬럼의 데이터(오름차순)으로 정렬
select * from melon_chart order by ranking;

-- melon_chart테이블의 모든 데이터를 ranking컬럼의 데이터(내림차순)으로 정렬
select * from melon_chart order by ranking desc;

-- melon_chart 테이블의 singer컬럼에서 '정국', '박재정'을 제외한 데이터들을 song 컬럼 기준으로 오름차순 정렬
select * from melon_chart where singer not in ('정국', '박재정') order by song;

-- melon_chart테이블에서 singer 컬럼을 오름차순으로 정렬하고 같은 singer 값에 대해서는 like_no컬럼을 내림차순으로 정렬
select * from melon_chart order by singer asc, like_no desc;
```