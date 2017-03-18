# 컬랙션

## Collection Framework(컬랙션 프래임워크)
__프레임워크__ 란 하나의 틀, 규칙, 룰

프로그래밍에 필요한 다양한 자료구조들을 제네릭 형식으로 제공해주는 라이브러리이다.

* collection interface
  * set
  * list
    * ArrayList
    * LinkedList
  * queue
* Map

***
# ArrayList*
* 순서를 가지는 원소들의 모임으로 원소들은 중복이 가능하다.
* __위치__ 를 이용하여 원소에 접근한다.
* 가변으로 리스트의 크기가 __자동조정__ 된다.
* 배열과 비슷하지만 크기가 동적으로 자동조정된다.__가변크기배열__ 이라고 보면된다.

## 장점
* 인덱스를 이용한 접근이 빠르다.
* 자료를 찾는데 빠르다.
* 실시간 처리에 적합하다.

## 단점
* 확장할 때 마다 새로운 ArrayList를 만들어 기존의 ArrayList를 복사한뒤 하나를 추가하는 방식이라 효율이 안좋다.
* 데이터들이 계속해서 가변적으로 바뀌게 되면 효율이 떨어진다.
* 삭제 할때 삭제된 데이터를 빼고 새로운 ArrayList에 복사를 한다.

* * *

# LinkedList
* ArrayList를 빈번하게 사용하여 삽입,삭제 등을 할 경우에 발생하는 문제를 개선하였다.
* 연결리스트로 구현되어 있다.(이중연결리스트)
* 삽입이나 삭제시 링크 값만 변경하면 된다.
* 인덱스로 원소에 접근하는 때는 ArrayList보다 시간이 많이 걸린다.

|연결리스트 구조|
|-------|
|연결부|
|데이터부|
|노드|
```
연결리스트는 add가 일어나면 노드라는 것을 만들게 된다.
노드가 add된 새로운 연결리스트의 연결부에 연결이 되어 데이터를 저장하게된다.
```
## 장점
* 추가, 삭제에 유리하다.
* 동적인 자료 처리에 유리하다.
* 자원관리의 효율이 좋다.
## 단점
* 인덱스로 원소 접근 시 시간이 많이 걸린다.
* 제일 앞의 주소만 알고 있다. 그래서 찾고자 하는 위치 만큼 다음 주소로 이동해야한다.
* 탐색에 대한 효율이 안좋다.

# Iterator(반복자)
연결부를 이용하여 다음(이전) 원소를 탐색한다.

1. 하나의 데이터를 삭제 할때면 인덱스를 사용
2. 동시에 여러개의 데이터를 삭제 할때는 Iterator를 사용하는게 좋다.

|메소드|설명|
|-------|-|
|hasNext()|방문 하지 않은 원소가 있다면 true|
|next()|다음 원소를 반환|
|remove()|최근 반환했던 원소를 삭제|

# ArrayList, LinkedList 예제

리스트 계열의 컬랙션 프래임워크
1) 자료의 저장 순서가 있다.(인텍스를 사용할 수 있다.)  
2) 중복된 자료의 지정이 가능하다.

ArrayList : 배열 기반  
데이터가 추가 될 때마다 배열을 새로 만들고 전에 있던 데이터를 복사  
LikedList : 연결리스트 기반  
데이터가 추가 되면 노드가 하나 늘어 난다.(노드끼리 연결)


(1) add : 요소(원소) 추가  
(2) remove : 삭제  
(3) get : 참조 구하기(가져오기)  
(4) set : 바꾸기(수정하기)  
```
    ArrayList<String> arrayList = new ArrayList<>();
		arrayList.add("B");
		arrayList.add("C");
		arrayList.add("A");

    //List의 길이를 얻는 메소드 size();
		for(int i = 0 ; i<arrayList.size() ; i++){
			System.out.println(arrayList.get(i));
		}
		System.out.println();
		//수정하기
		arrayList.set(1, "D");
		System.out.println(arrayList.get(1));

		System.out.println();
		//삭제하기
		System.out.println(arrayList);
		arrayList.remove(1);			//인덱스로 삭제
		arrayList.remove("B");
		arrayList.remove("A");

		System.out.println(arrayList);
```
* _ArrayList는 중복된 자료의 저장을 허용한다._

```
    ArrayList<Apple> appleList = new ArrayList<>();
		Apple apple1 = new Apple();

		appleList.add(apple1);
		appleList.add(apple1);

		System.out.println(appleList);
```
# set(집합)  
- __순서에 상관없이__ 원소만 저장하고 싶을 때 사용한다.  
- __중복 허용을 하지 않는다.__  
-잘알려진 방법으로는 __해쉬테이블__ 이다.
* hash set(해쉬 알고리즘)  
* tree set(트리 알고리즘)

|set의 구조(집합의 형태임)|
|-------|
|A, B, C|
|D, E, F|
|_A_ 안됨, _B_ 안됨(중복 X)|

### 해쉬테이블
객체의 메모리 주소값을 10진수 정수 형태로 표현.

### 트리셋
- 정렬의 기준이 존재

```
리스트        / set의 다른점
중복저장허용  / 안함
순서가 있다   / 없다

```
# Map <K, V>
제네릭이 2개이다.  
등록시 put(키값, 밸류값)
얻을때 키값으로 밸류 값을 받아 온다.
