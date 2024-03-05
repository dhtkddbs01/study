# CREATE
1. create문으로 데이터베이스에 테이블 생성
2. 테이블을 생성할 시에는 테이블명, 컬럼명, 컬럼의 데이터탕비, 사이즈, 필수 여부 등에 대한 정의가 되어야 한다.
3. 테이블명은 숫자로 시작할 수 없고 '_', '$'외의 특수 기호는 사용할 수 없다.
```sql
-- 데이터 베이스 목록 출력
show database;

-- 사용할 데이터베이스 선택
use mysql;

-- book_list라는 이름의 테이블을 생성
create table book_list(
    -- 긴 숫자는 int 담을 수 없기 때문에 varchar타입이고 최대 16자리로 설정
    -- 데이터가 필수로 존재해야 하기 때문에 null일 수 없다.
    book_no     varchar(16) not null,
    book_name   varchar(50),
    writer      varchar(50),
    publisher   varchar(30),
    -- 날짜 형식의 데이터가 들어갈 예정이기 때문에 date형식으로
    reg_date    date,
    -- 계산을 하는 로직들이 사용될 것이기 때문에 varchar대신에 int
    price       int
);
```
