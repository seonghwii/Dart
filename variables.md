Dart Basic
===
### 1. dart : 객체 지향 언어
### 2. flutter : 객체 지향 프레임워크(class 사용)
### 3. Entry Point (main 함수)
* Entry Point란?    
프로그램이 시작하는 시점 ([자세히보기](https://min-mon.tistory.com/entry/Entry-Point))
### 4. 끝에 꼭 ';' 기재(cascade operator 기능 때문. 추후 설명 예정)
### 5. dart의 기본적인 변수는 non-nullable이다.
---
  
Variables
===
> ## Var
### 1. 변수 선언       
- 메소드 / 함수 내에서의 지역 변수 선언할 때

```dart
void main() {
    var name='cong';   
    print(name);
}
```
- class, property에서 변수 선언할 때

```dart
void main() {
    int i = 12;
    print(i);
}
```
> ## final

### 변수의 값을 수정하고 싶지 않을 때 사용
```dart
void main() {
    final name = 'cong';
    name = 1; // 에러 발생
}
```
> ## dynamic
### 어떤 데이터가 들어올 지 모를 때 사용
```dart
void main() {
    dynamic name;
    if (name is String) {
        name.isEmpty;
        name.isNotEmpy;
    }

}
```
변수 타입이 String인 경우, 변수의 값에 대해 위와 같이 체크해볼 수 있다.

```dart
void main() {
    dynamic name;
    if (name is int){
        name.isEven;
    }
}
```
변수 타입이 int인 경우, 짝수, 홀수, 무한의 여부 등을 체크할 수 있다. 

## ★ dart의 장점
조건문을 통해 변수의 타입을 지정해줄 때는 dart에서 그 타입에 맞는 속성들을 사용할 수 있게 해줌.

> ## const
### 컴파일할 때 값을 알고 있는 변수 생성
```dart
void main() {
    const name = 'cong';
    name = '12'; // 불가능(1)
    
    const gender = fetchApi(); // 불가능(2)

    const max_allowed_price = 120; 
}
```
__불가능(1)__    
: const는 final과 마찬가지로 데이터 초기화 이후 다른 값으로 업데이트 할 수 없다.
* __final과의 차이점?__   
final은 런타임 중에 만들어질 수 있다. (사용자가 앱을 실행하면서 변수를 만들 수 있다.)     
반면, const로 선언한 변수는 컴파일 하기 전에 값을 알고 있어야 한다.

__불가능(2)__  
: const로 선언한 변수는 컴파일 하기 전에 값을 알고 있어야 하기 때문에 값을 받아와야 하는 변수로 지정해주는 것은 적절하지 않다.

---
아래와 같은 경우에는 const를 사용할 수 없다.
1. 값을 모를 때
2. API에서 값을 받아올 때
3. 사용자의 앱을 통해 데이터를 받아야 할 때

그럴 경우에는 <span style="color:red">final</span>이나 <span style="color:red">var</span>로 변수를 선언해주어야 한다.

---
> ## null-safety
### 잘못된 상태의 변수(null)를 참조하는 걸 막아주는 기능
```dart
bool isEmpty(String string) => string.length == 0;

void main() {
    isEmpty(null);
}
```

#### null safety가 없는 dart 버전에서 실행할 경우, '__NoSuchMethoderror__'가 뜬다. 
1.  변수 타입이 String인 값을 넣어 주어야 하는데 null을 넣어주었기 때문.   
2. null을 보내준 다음에 string의 length라는 속성에 접근   
3. null에는 length라는 속성이 없기 때문에 에러 발생   


---
### __null의 상태를 나타내고 싶을 때__  
```dart
void main(){
    String? name = 'cong';
    name = null;
    name.length;
}
```
위와 같이 변수타입(String) + "?"를 붙여줄 경우, 변수(name)에 대한 값이 null일 수도 있다는 것을 dart에게 알려준다.

```dart
void main(){
    String? name='cong';
    name = null;
    if (name != null){
        name.isNotEmpty;
    }

    // 위와 동일한 단축 문법
    name?.isNotEmpty; // name이 null이 아닐 경우에 isNotEmpty를 반환한다.
}
```
> ## Late
### 변수를 데이터로 초기화해주지 않고 변수만 선언해줄 때 사용하는 기능   
##### (flutter로 API를 통해 값을 가져올 때 유용하게 사용하는 기능)  
```dart
void main() {
    late final String name;
    name = '';
    print(name);
}
```
1. late는 초기에 변수 선언 없이 변수를 사용할 수 있게 해 준다.
2. API에서 값을 보내주면 late로 선언한 변수에 값을 넣어 준다. 
---



