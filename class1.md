Dart - Class(1)
===
> ## Class 기본 구조
```dart
class Player { 
  String name = 'cong'; 
  int xp = 1500;

}

void main(){ 
  var player = Player(); 
  print(player.name);
  player.name = 'lalalala';
  print(player.name);
}
```
1. class이기 때문에 변수 타입을 꼭 지정해주어야 한다.
2. class 객체를 생성해줄 때는 new를 붙여주지 않아도 된다.

**변수 name의 값을 고정해두고 싶을 때 (final 사용)**
```dart
class Player { 
  final String name = 'cong';
  int xp = 1500;

}
```
**class의 값을 text에 반영하고 싶을 때**
```dart
class Player { 
  String name = 'cong';
  int xp = 1500;

  void sayHello() {
    print("Hi my name is $name");
  }
}
```
- dart 언어의 특징 : text에서 변수를 호출할 때 this를 사용하지 않아도 된다.

```dart
class Player { 
  String name = 'cong';
  int xp = 1500;

  void sayHello() {
    var name = '121';
    print("Hi my name is ${this.name}");
  }
}
```
- 단, 위와 같이 동일한 이름의 변수명이 class에 있는 경우에는 정확한 변수를 가르키기 위해 this를 사용한다.   


> ## Constructors
```dart
class Player { 
  late final String name;
  late int xp;

  Player(String name, int xp){
    this.name = name;
    this.xp = xp;
    
  }

  void sayHello() {
    print("Hi my name is $name");
  }
}

void main(){ 
  var player = Player("cong", 1500); 
  player.sayHello(); 
  var player2 = Player("long", 1600); 
  player2.sayHello();
}

>> Hi my name is cong
   Hi my name is long
```
1. 값을 미리 선언해주지 않았기 때문에 late로 변수만 먼저 선언해준다.
2. main 함수에서 생성자를 만들어준 후, sayHello 메소드를 호출해준다.

### 생성자 축약 방법
```dart
class Player { 
  final String name; 
  int xp;

  Player(this.name, this.xp); 

  void sayHello() {
    print("Hi my name is $name");
  }
}

void main(){ 
  var player = Player("cong", 1500); 
  player.sayHello(); 
  var player2 = Player("long", 1600); 
  player2.sayHello();
}
>> Hi my name is cong
   Hi my name is long
```

> ## Named Constructor Parameters
### **positional argument**
```dart
class Player { 
  final String name;
  int xp;
  String team;
  int age;

  Player(this.name, this.xp, this.team, this.age);

  void sayHello() {
    print("Hi my name is $name");
  }
}

void main(){ 
  var player = Player("cong", 1500, 'red', 12); 
  player.sayHello(); 
  var player2 = Player("long", 1600, 'blue', 12); 
  player2.sayHello();
}
```
### **named argument** 
```dart
class Player { 
  final String name;
  int xp;
  String team;
  int age;

  Player({
    required this.name, 
    required this.xp, 
    required this.team, 
    required this.age
    });

  void sayHello() {
    print("Hi my name is $name");
  }
}

void main(){ 
  var player = Player(
    name : "cong", 
  xp : 1500, 
  team : 'red', 
  age : 12); 
  player.sayHello(); 
  var player2 = Player(
    name : "long", 
    xp : 1600, 
    team : 'blue', 
    age : 12); 
  player2.sayHello();
}
```
1. 생성자 파라미터 {} 추가
2. null safety 고려하여 파라미터에 required 추가
> ## ★ Named Constructors
```dart
class Player { 
  final String name;
  int xp;
  String team;
  int age;

  Player({
    required this.name, 
    required this.xp, 
    required this.team, 
    required this.age
    });

  Player.createBluePlayer({
    required String name,
    required int age,
  }) :this.age = age,
      this.name = name,
      this.team = 'blue',
      this.xp = 0;

  void sayHello() {
    print("Hi my name is $name");
  }
}

void main(){ 
  var player = Player.createBluePlayer(
    name : "cong", 
  age : 12
  );
}
```
### 하나씩 살펴보자.
1. 클래스 생성
    ```dart
    class Player { 
    final String name;
    int xp;
    String team;
    int age;
    }
    ```
2. Play객체 생성
    ```dart
    Player({
        required this.name, 
        required this.xp, 
        required this.team, 
        required this.age
        });
    ```

3. Play객체 초기화 작업
    ```dart
    Player.createBluePlayer({
        required String name,
        required int age,
        }) :this.age = age,
            this.name = name,
            this.team = 'blue',
            this.xp = 0;
    ```
    - play 객체 생성  
    - Play 객체 초기화(**_콜론(:)_ 입력**)

- ### **positional argument** : createRedPlayer
- ### **named argument** : createBluePlayer
```dart
class Player { 
  final String name;
  int xp;
  String team;
  int age;

  Player({
    required this.name, 
    required this.xp, 
    required this.team, 
    required this.age
    });

  Player.createBluePlayer({
    required String name,
    required int age,
  }) :this.age = age,
      this.name = name,
      this.team = 'blue',
      this.xp = 0;

  Player.createRedPlayer(
    String name,
    int age,
  ) : this.age = age,
       this.name = name,
       this.team = 'Red',
       this.xp = 0;


  void sayHello() {
    print("Hi my name is $name");
  }
}

void main(){ 
  var player = Player.createBluePlayer(
    name : "cong", 
  age : 12
  );

  var player2 = Player.createRedPlayer(
    "long", 
    12); 
}
```
> ## Recap
### 전체 코드
```dart
class Player { 
  final String name;
  int xp;
  String team;

  Player.fromJson(Map<String, dynamic> playerJson): 
  name = playerJson['name'], 
  xp = playerJson['xp'],
  team = playerJson['team'];


  void sayHello() {
    print("Hi my name is $name");
  }
}

void main(){ 
  var apiData = [
    {
      "name" : "cong",
      "team": "red",
      "xp":0,
    },
    {
      "name" : "lynn",
      "team": "red",
      "xp":0,
    },
    {
      "name" : "dal",
      "team": "red",
      "xp":0,
    },
  ];

  apiData.forEach((playerJson) {
    var player = Player.fromJson(playerJson);
    player.sayHello();
    
    });


}
```
- 세부 설명  
1. Player 클래스 생성
  ```dart
  class Player { 
    final String name;
    int xp;
    String team;
    }
  ```
2. Player.fromJson 생성자 생성(Player 클래스의 property 초기화)
  ```dart
  Player.fromJson(Map<String, dynamic> playerJson):
    name = playerJson['name'], 
    xp = playerJson['xp'],
    team = playerJson['team'];
  ```
3. main 함수에서 데이터 주고 생성자 호출
  ```dart
  void main(){ 
  var apiData = [
    {
      "name" : "cong",
      "team": "red",
      "xp":0,
    },
    {
      "name" : "lynn",
      "team": "red",
      "xp":0,
    },
    {
      "name" : "dal",
      "team": "red",
      "xp":0,
    },
  ];

  apiData.forEach((playerJson) {
    var player = Player.fromJson(playerJson);
    player.sayHello();
    
    });

  >> Hi my name is cong
     Hi my name is lynn
     Hi my name is dal
  ```
  - forEach(value) : List나 Set 형태의 값을 출력할 때 사용
    
