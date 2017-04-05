# mvc2(Model View Controler)
: mvc1 패턴이 있어 따로 관리하려 했지만, 아직 디자인과 구현부의 구분이 애매 모호 하여
mvc2패턴이 나오게 되었다

* 데이터 관련 모델링

## MVC를 쪼개서 보자
### Model
#### DAO(Data Access Object)
1. Data Base
: table
2. SQL
3. SQL 결과물 - > 클래스화 (DTO)
#### DTO(Data Transfer Object) / VO(Value Object / Visual Object)
:서버가 클래스에게 보내는 데이터를 객체화 해놓는 것이다.
_Spring framework 떄 실습 해보자_
DAO의 결과물을 저장하는 클래스

```
VO{
    맴버변수
    getter/setter()
}
```
### View
:(=jsp) 데이터베이스에 가져오고, 비지니스로직이 들어가고 이런부분은 필요가 없게된다.
* Model의 결과물
* 클라이언트에게 전달

## Controler
: 비지니스 로직에 해당된다.

### mvc2 모델의 과정 및 설명
`Client` -> `Controler` -> `Service` - > `DAO` -> `Data Base` ->  `DAO` - > `Sever` - > `Controler` -> `View` - > `Client`

`Controler`(servlet) : request 패킷 분석(url,패킷), parameter 가져오기
`Service` : 부가 서비스(비지니스 로직),DAO 호출(데이터베이스 접근)
`View` : response의 데이터를 출력할 페이지
`View`-`Client` : response로 페이지를 보여준다.
