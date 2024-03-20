# CASE WHEN
case col
when val1 then result1
when val2 then result2

위와 동일

case when col = val1 then res1
     when col = val2 then res2
else val end     
```sql
select * from employee;

# gener가 F면 여자 M이면 남자로 변경
select emp_nm,
    case gender
    when 'F' then '여자'
    when 'M' then '남자'
    else '해당없음' end as gender
 from employeel

# gener가 F면 여자 M이면 남자로 변경
select emp_nm,
        case when gender = 'F' then '여자'
             when gender = 'M' then '남자'
        else '해당없음' end as gender
    from employee;

# hire_dt가 2023년1월1일보다 크면 신규사원, 아니면 기존사원으로 emp_type컬럼에 저장
select emp_nm, hire_dt,
        case when hire_dt > '20230101000000' then '신규사원'
        else '기존사원' end as emp_type
    from employee;

# 2022년 1월 1일 이하인 사원들이 옛날 사원이 아닌 기존사원으로 저장됨
# case when은 위에서부터 한줄씩 비교하고 해당하면 밑에 비교문 X
select emp_nm, hire_dt,
        case when hire_dt < '20230101' then '기존사원'
             when hire_dt < '20220101' then '옛날사원'
        else '신규사원' end as emp_type
    from employee
```