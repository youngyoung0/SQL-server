# 일괄처리, select-list, Row-to-col

생성일: 2021년 11월 25일 오후 10:42

### 일괄처리

- 데이터 베이스를 백업한 후 복원하기 위해서 일괄처리 합니다.
- cmd→ mysql→ 해당하는 .sql 파일 실행

### select-list

- select 사용시 순서에 따른 줄번호 활용

```sql
select
	@num := @num+1 as num,
    idx, title, content
from (select@num:=0) a,
	board b
order by idx desc;
```

![Untitled](%E1%84%8B%E1%85%B5%E1%86%AF%E1%84%80%E1%85%AA%E1%86%AF%E1%84%8E%E1%85%A5%E1%84%85%E1%85%B5,%20select-list,%20Row-to-col%203549dbf401684b3eaa2fb427f59a3034/Untitled.png)

초기값 설정은 → (select @num:=10) a

### Row-to-col

![Untitled](%E1%84%8B%E1%85%B5%E1%86%AF%E1%84%80%E1%85%AA%E1%86%AF%E1%84%8E%E1%85%A5%E1%84%85%E1%85%B5,%20select-list,%20Row-to-col%203549dbf401684b3eaa2fb427f59a3034/Untitled%201.png)

```sql
select id,
	sum(case when name='A' then value else 0 end) as 'A',
	sum(case when name='B' then value else 0 end) as 'B'
from item
group by id;
```

![Untitled](%E1%84%8B%E1%85%B5%E1%86%AF%E1%84%80%E1%85%AA%E1%86%AF%E1%84%8E%E1%85%A5%E1%84%85%E1%85%B5,%20select-list,%20Row-to-col%203549dbf401684b3eaa2fb427f59a3034/Untitled%202.png)