# HAVING
1. GROUP BY와 ORDER BY 사이에 작성
```SQL
-- 오류 발생
select animal, type, count(*) from animal_info where count(*) > 2 group by animal, type;

-- animal_info 테이블에서 animal별, type별로 '고양이' 데이터를 그루핑하고 데이터 개수 파악 후 2개 이상인 것만 오름차순 출력
select animal, type, count(*) 
    from animal_info 
    where animal = '고양이'
    group by animal, type 
    having count(*) > 2 
    order by count(*) desc;
```    