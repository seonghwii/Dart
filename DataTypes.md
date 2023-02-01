Dart - Data Types
===

> ## 기본 데이터 타입

```dart
void main() {
    String name = "nico";
    bool alive = true;
    int age = 12;
    double money = 69.99;
}
```

- dart의 대부분은 object로 이루어져 있다.      
    1.  String, bool : class
    2.  int, double : num을 상속받은 클래스(즉, num의 자녀 클래스)     
        ```dart
        void main() {
        num age = 12;
        }
        ```
        num이 int, double의 부모 클래스이다.   
        따라서 위와 같이 변수를 선언해줄 경우, age의 타입은 int 혹은 double이 될 수 있다.   

> ## list 사용법

- 함수나 메소드 안에 지역 변수로 사용할 때

    ```dart
    void main() {
        var numbers = [1, 2, 3, 4];
    }
    ```
- class나 property에서 변수로 사용할 때      

    ```dart
    void main() {
        List<int> numbers = [1, 2, 3, 4];
    }
    ```
    값을 업데이트 할 때는 해당 자료형만 넣을 수 있다.

> ## collection if
```dart
void main(){
    var giveMeFive = true;
    var numbers = [
        1,
        2,
        3,
        4,
        if (giveMeFive) 5, 
    ];
}
```

위 문법은 아래와 같다.       
```dart
void main(){
    var giveMeFive = true;
    var numbers = [
        1,
        2,
        3,
        4,
    ];
    if (giveMeFive) {
        numbers.add(5);
    } 
}
```
> ## String Interpolation
- 단순히 변수 값을 담고 싶을 때 = '$변수명'
```dart
void main(){
    var name = 'cong';
    var greeting = 'Hello everyone, my name is $name, nice to meet you!';
    print(greeting);
}
```

-  무언가 계산하고 싶을 때 = '$변수명 + {실행할 부분}'   
```dart
void main(){
    var name = 'cong';
    var age = 10;
    var greeting = 'Hello everyone, my name is $name and ${age + 2}';
    print(greeting);    
}
```
>## collection for   
  두개의 리스트가 있을 때, 하나의 리스트에 있는 값을 또 다른 하나의 리스트에 넣어줄 수 있다.

```dart
void main(){
    var oldFriends = ['cong', 'miyeok'];
    var newFriends = [
    'lewis',
    'ralph',
    'darren',
    for (var friend in oldFriends) "★ $friend",

    ];
    print(newFriends);

}
```

이 문법은 아래와 같다.
```dart    
void main(){
    var oldFriends = ['cong', 'miyeok'];
    var newFriends = [
    'lewis',
    'ralph',
    'darren',
    ];

    for (var friend in oldFriends) {
    newFriends.add("★ $friend");
    }
    print(newFriends);
}
```
- 주 사용 : UI 작업 / navigation bar 등등   
> ## Maps
python의 dictionary 같은 기능   
```dart
void main(){
    var player = { 
        'name' : 'cong',
        'xp': 19.99,
        'superpower': false,
    };
}
```

1. var로 선언할 경우, 자동으로 변수의 타입이 선언된다.   
2. dart는 기본적으로 object 타입이기 때문에 value의 형식을 통일해주지 않으면 자체적으로 object로 인식한다. 즉, player의 변수 타입 = (Map<String, object>) 

 - 명시적으로 형식을 지정해줄 경우, 빈 Map 생성 가능    
    ```dart            
    void main() {
        Map<int, bool> player = {
        1:true,
        2:false,
        3:true
            };
    }
    ```

- key값을 List로도 사용 가능   
    ```dart
    void main(){
        Map<List<int>, bool> player = {
            [1, 2, 3, 5]:true,
        };
    }
    ```

- Map List 생성 가능   
    ```dart
    void main(){
        List<Map<String, Object>> player = [
            {
            'name': 'cong',
            'age' : 26,
            }
        ];
    }
    ```

Map도 class, property를 가지고 있다. (자세히 보기를 추천함.)

key와 value를 가지는 구조로 object를 만들 때, 그것이 특정 형태를 가질 때, API로 얻은 데이터는 class로 다루는 것을 추천.

> ## Sets
1. Set은 중복 값을 넣을 수 없다.
2. 선언      
    ```dart
    void main(){
    var numbers = {1, 2, 3, 4};
    }
    ```
    혹은 이렇게 쓸 수 있다.
    
    ```dart
    void main(){
    Set<int> numbers = [1, 2, 3, 4];
    }
    ```

3. 값 추가하는 방법   
    ```dart
    void main(){
        var numbers = {1, 2, 3, 4};
        numbers.add(1);
        numbers.add(1);
        print(numbers);
    }

    >> {1, 2, 3, 4}
    ```
    *set은 중복값을 허용하지 않기 때문에 보유 중인 값을 넣어줄 경우, 소멸된다. 
