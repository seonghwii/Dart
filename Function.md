Dart - Functions
===
> ## Function 기본 구조
```dart
void sayHello(String name) { 
  print("Hello $name nice to meet you");
}
```
void :함수는 아무것도 리턴해주지 않는다는 의미
```dart
String sayHello(String name) { 
  return "Hello $name nice to meet you";
}
```
위와 같이 리턴 타입을 'String'으로 줄 경우, 함수의 리턴값을 String으로 주어야 한다.   

- 함수가 하나의 값만 리턴할 때(**_far arrow syntax_** 사용)
```dart
String sayHello(String name) => "Hello $name nice to meet you"; 

num plus(num a, num b) => a + b;
```
이런 형태로 사용할 수 있다.

> ## Named Parameters  
### **_positional argument_**   
```dart
String sayHello(String name, int age, String country) { 
  return "Hello $name, you are $age, and you come from $country;";
}

void main(){ 
  print(sayHello('cong', 20, 'cuba'));
}
```
사용자가 파라미터 각각의 위치를 기억해야 한다는 단점이 있다.
### **_named argument_**   
main 함수에서 sayHello 함수를 호출할 때, 사용자가 parameter의 순서와 값을 헷갈리지 않고 넣어주기 위한 기능
### **사용 방법**
1) parameter에 '{}'를 넣어준다.  
2) main 함수에서는 parameter의 이름과 argument 값을 함께 기재해준다.
    
    ```dart
    String sayHello({String name, int age, String country,}) { 
        return "Hello $name, you are $age, and you com from $country;";
    }

    void main(){ 
    print(sayHello(
        name : 'cong',
        age : 20,
        country : 'cuba',
        ));
    }
    ```
    * **parameter**의 순서는 상관 없다.  

### **고려사항** 

dart는 null safety를 제공하므로 특정 parameter에 대한 값이 null일 때를 고려한다.    
따라서 경우에 따라 아래의 작업을 해주어야 한다.  
1. 파라미터에 대한 기본 값을 지정해줘도 문제가 없는 경우, default value값 설정 

    ```dart
    String sayHello({
        String name='anon', 
        int age=50, 
        String country='wakanda',
        }) { 
        return "Hello $name, you are $age, and you come from $country;";
    }

    void main() {
        print(sayHello());
    }
    ```
    이 경우 main 함수에서 sayHello 함수를 호출할 때 argument를 넣어주지 않아도 된다.    
2. 사용자에게 값을 꼭 입력 받아야할 경우, required modifier 설정
    ```dart
    String sayHello({
        required String name, 
        required int age,
        required String country,
        }) { 
        return "Hello $name, you are $age, and you come from $country;";
    }

    void main() {
        print(sayHello(
            age : 12,
            country : 'wakanda',
            name = 'cong',
        ));
    }
    ```
### **parameter VS argument의 차이점?**  
 
```dart
num plus(num a, num b) => a + b;
```
1. parameter(파라미터) : 함수/메서드 입력 변수명   
▷ 위에서 parameter는 'a, b'이다.
```dart
void main() {
    print(plus(2, 3));
}
```
2. argument(인자) : 함수/메서드 입력 값   
▷ 위에서 argument는 '2, 3' 이다.  

> ## Optional Positional Parameters
```dart
String sayHello(String name, int age, String country) => 
   "Hello $name, you are $age, and you come from $country;";


void main(){ 
  sayHello('cong', 20, 'cuba');
}
```
만약 특정 parameter를 필수로 요청받고 싶지 않은 경우, 아래와 같이 사용할 수 있다.  
```dart
String sayHello(
    String name, 
    int age, 
    [String? country = 'cuba']
) => 
   "Hello $name, you are $age, and you come from $country;";
```
1. 대괄호[] 표시
2. 해당 parameter에 'null'값일 수도 있음을 알려주는 '?' 표시
3. default value 설정

```dart
void main() {
    var results = sayHello('cong', 20);
    print(results);
}

>> Hello cong, you are 20, and you come from cuba;
```
> ## QQ Operator ( "**??**" )

```dart
 String capitalizeName(String? name) => name.toUpperCase();

void main(){ 
  capitalizeName('cong');
  capitalizeName(null);
}
```
위의 경우, capitalizedName 메소드의 리턴 타입에 이슈가 생긴다.  
메소드의 argument(인자) 값이 null일 수도 있기 때문이다.  
이 경우, 아래와 같이 해결할 수 있다.

1. 첫번째 방법
    ```dart
    String capitalizeName(String? name) {
    if (name != null) {
    return name.toUpperCase();
    }
    return 'ANON';
    }
    ```
2. 두번째 방법( ?  : 사용)
    ```dart
    String capitalizeName(String? name) => name != null ? name.toUpperCase() : 'ANON';
    ```
   **해석**] 조건문 ? (True일 때 실행문) : (False일 때 실행문)

3. 세 번째 방법( ?? 사용)  
    ```dart
    String capitalizeName(String? name) => name?.toUpperCase() ?? 'ANON';
    ```
    - (LEFT) ?? (RIGHT)  
        1. (LEFT) == NULL > (RIGHT) 리턴  
        2. (LEFT) != NULL > (LEFT) 리턴

> ## QQ assignment operator
```dart
void main(){ 
  String? name;
  name ??= 'cong';
  name ??= 'another';
  print(name);
}

```    
    >> Warning: Operand of null-aware operation '??=' has type 'String' which excludes null.
1. name 변수 선언(변수 타입 : String or null 값)
2. name이 null일 때, name = 'cong'
3. name이 null이 아니므로 'name ??= 'another';' 에서 Warning!

> ## typedef
### 자료형이 헷갈릴 때 도움이 될 alias를 만드는 기능
```dart
typedef ListOfInts = List<int>;

ListOfInts reverseListOfNumbers(ListOfInts list) {
  var reversed = list.reversed;
  return reversed.toList();
}


void main(){ 
  print(reverseListOfNumbers([1, 2, 3]));
}
```
- typedef alias = 변수 타입;  
이렇게 지정해주면 변수 타입이 놓일 자리 → alias로 대치 가능

- 구조화 데이터를 다루고 싶을 경우, class 사용!