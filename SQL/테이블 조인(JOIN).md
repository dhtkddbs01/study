# INNER JOIN
```SQL
select * from world_tour1;

select * from world_tour2;

# wt1(world_tour1) 테이블과 wt2(world_tour2) 테이블에서 world_tour1.cast = world_tour2.cast인 데이터만 합치기
select * from world_tour1 wt1 inner join world_tour2 wt2 on wt1.cast = wt2.cast;

# wt1(world_tour1) 테이블과 wt2(world_tour2) 테이블에서 world_tour1.cast = world_tour2.cast인 데이터만 합치고 wt1의 cast컬럼 데이터 출력
select wt1.cast from world_tour1 wt1 inner join world_tour2 wt2 on wt1.cast = wt2.cast;

# 위의 inner조인과 같은 결과 출력
select wt1.cast from world_tour1 wt1, world_tour2 wt2 where wt1.cast = wt2.cast;
```

# OUTER JOIN
- LEFT OUTER JOIN 과 RIGHT OUTER JOIN 존재 (합칠 테이블 기준)
```SQL
select * from world_tour1;
select * from world_tour2;

# wt1테이블은 모두 출력하고 wt2는 join에 성공한 데이터만 출력
select * from world_tour1 wt1 left outer join world_tour2 wt2 on wt1.cast = wt2.cast;

# wt2테이블은 모두 출력하고 wt1는 join에 성공한 데이터만 출력
select * from world_tour1 wt1 right outer join world_tour2 wt2 on wt1.cast = wt2.cast;
```
