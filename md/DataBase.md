# 데이터 베이스

## 데이터베이스의 정의
: 데이터가 상이한 목적을 가진 여러 응용에 중복되어 사용 될수 있다는 공용 개념에 기초를 두고 있습니다.  
여러 응용 시스템들이 공용 할 수있도록 통합, 저장된 운영 데이터의 집합
1. 통합된데이터  
:
2. 저장된 데이터  
:
3. 운영 데이터  
:
4. 공용 데이터  
:

## 데이터 베이스 특징
1. 실시간 접근성  
:
2. 지속적인 변화  
:
3. 동시 공유  
:
4. 내용에 의한 참조  
:

# 데이터베이스 관리 시스템(DBMS Data Base Management System)  
: 데이터베이스를 관리 할 수 있는 환경을 제공.

`응용프로그램들` - `데이터베이스 관리 시스템(DBMS)` - `데이터베이스`

## 관계형 데이터베이스 관리 시스템
* 확장이 용이하다.  
: 데이터베이스를 만든 후 관련되는 데이터들을 이용하는 응용 프로그램들을 변경하지 않고도, 새로운 데이터 항목을 데이터베이스에 추가 할 수 있다.
* 정보를 저장하기 위한 구조로 테이블을 이용합니다.  
: ROW, Colume으로 구성합니다.
* SQL(Structed Query Language)  
: 사용자와 관계형 데이터베이스를 연결시켜 주는 표준 검색언어이다. 데이터베이스에 있는 데이터를 직접 조회하거나 또는 보고서를 추출하는데 사용됩니다.

# SQL과 SQL Plus의 개념

* SQL이란  
: 질의 언어를 통해서 데이터베이스에 저장된 데이터를 조회, 입력, 수정 삭제하는 등의 조작이나, 테이블을 비롯한 다양한 객체(시퀸스, 인덱스 등)를 생성 및 제어하는 역할
> 1) 데이터 정의어(DDL)  
: 논리적 구조를 정의 하기 위한 언어
> 2) 데이터 조작어(DML)  
: 저장된 데이터를 조작하기 위해 사용하는 언어
> 3) 데이터 제어어(DCL)  
: 데이터에 대한 접근 권한 부여, 시스템의 트랜잭션을 관리하기 위한 목적으로 사용되는 언어 입니다.

* SQL명령어는 여러개의 `절` 이 모여서 문장이 되고 문장은 반드시 세미콜론(;)으로 마쳐야 한다.
* 일반적으로 한 줄에 하나의 절을 입력하는 것이 좋다.(가독성 향상)

## SELECT
: SELECT문은 테이블에 저장된 데이터를 조회하는데 사용되는 SQL

형식
```
SELECT [DISTINCT] {*,Colume[Alias],...,}
```
`[]는 생략 가능한 내용을, {}안의 기술한 내용중 하나 이상은 적어야함.`

## DML  
:
1) INSERT  
:
2) UPDATE  
:
3) DELETE  
:
## TCL(Transaction Control Language)
: Transaction(작업의 원자성)은 해당작업이 끝나기전까지 멈추면 안됨
`COMMIT` : 작업이 완료되면 실행시켜준다. = 변경된 내용을 영구히 저장합니다.  
`ROLLBACK` :COMMIT을 하기전에 실행시 이전 상태로 되돌려준다.

## DDL(Data Definition Language)  
:
1) CREATE :
2) ALTER :
3) DROP :

## SQL Plus  
:

```
SQL> DESC EMP
 이름                                      널?      유형
 ----------------------------------------- -------- ----------------------------
 EMPNO                                     NOT NULL NUMBER(4)
 ENAME                                              VARCHAR2(10)
 JOB                                                VARCHAR2(9)
 MGR                                                NUMBER(4)
 HIREDATE                                           DATE
 SAL                                                NUMBER(7,2)
 COMM                                               NUMBER(7,2)
 DEPTNO                                             NUMBER(2)

// EMPNO : 사원번호, ENAME : 이름, JOB : 직책, MGR : 상사코드, HIREDATE : 고용일, SAL : 급여,   
COMM : 보너스 급여, DEPTNO : 부서
```

## 컬럼 이름에 별칭 지정하기

```
//기본 형태, AS를 가독이 좋게 적어주는 형태
SELECT ENAME, SAL*12 AS YearSal
FROM EMP;

//띄어 쓰기 가능, 하지만 띄어쓰기는 쓰지말것!!!
SELECT ENAME, SAL*12 "YearSal"
FROM EMP;

SELECT ENAME, SAL*12 YearSal
FROM EMP;

```
## 각 데이터에 문자열 붙이기
```
SQL> SELECT ENAME || '님' FROM EMP;

ENAME||'님'
--------------------------
SMITH님
ALLEN님
WARD님
JONES님
MARTIN님
BLAKE님
CLARK님
SCOTT님
KING님
TURNER님
ADAMS님

ENAME||'님'
--------------------------
JAMES님
FORD님
MILLER님

SQL> SELECT ENAME || '님' AS 이름 FROM EMP;

이름
--------------------------
SMITH님
ALLEN님
WARD님
JONES님
MARTIN님
BLAKE님
CLARK님
SCOTT님
KING님
TURNER님
ADAMS님

이름
--------------------------
JAMES님
FORD님
MILLER님

SQL> SELECT ENAME, 'IS A', JOB
  2  FROM EMP
  3  ;

ENAME                'ISA'    JOB
-------------------- -------- ------------------
SMITH                IS A     CLERK
ALLEN                IS A     SALESMAN
WARD                 IS A     SALESMAN
JONES                IS A     MANAGER
MARTIN               IS A     SALESMAN
BLAKE                IS A     MANAGER
CLARK                IS A     MANAGER
SCOTT                IS A     ANALYST
KING                 IS A     PRESIDENT
TURNER               IS A     SALESMAN
ADAMS                IS A     CLERK

ENAME                'ISA'    JOB
-------------------- -------- ------------------
JAMES                IS A     CLERK
FORD                 IS A     ANALYST
MILLER               IS A     CLERK

SQL> SELECT ENAME||'IS A', JOB
  2  FROM EMP
  3  ;

ENAME||'ISA'                 JOB
---------------------------- ------------------
SMITHIS A                    CLERK
ALLENIS A                    SALESMAN
WARDIS A                     SALESMAN
JONESIS A                    MANAGER
MARTINIS A                   SALESMAN
BLAKEIS A                    MANAGER
CLARKIS A                    MANAGER
SCOTTIS A                    ANALYST
KINGIS A                     PRESIDENT
TURNERIS A                   SALESMAN
ADAMSIS A                    CLERK

ENAME||'ISA'                 JOB
---------------------------- ------------------
JAMESIS A                    CLERK
FORDIS A                     ANALYST
MILLERIS A                   CLERK

SQL> SELECT ENAME||' IS A' AS 이름 , JOB
  2  FROM EMP;

이름                           JOB
------------------------------ ------------------
SMITH IS A                     CLERK
ALLEN IS A                     SALESMAN
WARD IS A                      SALESMAN
JONES IS A                     MANAGER
MARTIN IS A                    SALESMAN
BLAKE IS A                     MANAGER
CLARK IS A                     MANAGER
SCOTT IS A                     ANALYST
KING IS A                      PRESIDENT
TURNER IS A                    SALESMAN
ADAMS IS A                     CLERK

이름                           JOB
------------------------------ ------------------
JAMES IS A                     CLERK
FORD IS A                      ANALYST
MILLER IS A                    CLERK
```

## WHERE 조건과 비교 연산자

### 비교 연산자
|연산자|의미|
|:-------|:-------|
|=|같다|
|>|보다 크다|
|<|보다 작다|
|>=|보다 크거나 같다|
|<=|보다 작거나 같다|
|<>,!=,^=|다르다|
### 논리 연산자

|연산자|의미|
|:-------|:-------|
|AND|두가지 조건을 모두 만족해야만 검색할 수 있다.|
|OR|두가지 조건중 하나만 만족해도 검색할 수 있다.|
|NOT|조건에 만족하지 못하는 것만 검색한다.|

### LIKE 연산자


























***
여기가 끝
