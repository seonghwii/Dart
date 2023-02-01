Dart란?
===
### 1.Dart web
: dart로 쓴 코드를 javascript로 변환시켜주는 컴파일러

### 2. Dart native
: dart로 쓴 코드를 여러 CPU의 아키텍쳐에 맞게 변환시켜줌.     

---

Why Dart?
===
### 1. JIT(Just-In-Time), AOT(Ahead-Of-Time) 컴파일러 모두 사용 가능

- [개발 중] JIT(Just-In-Time) 컴파일러로 빌드   
런타임 시점에서 개발자가 짠 소스 코드를 기계어로 번역   
따라서, dart VM(Virtual Machine)을 통해 작성한 코드를 바로 볼 수 있음. (빠른 피드백 가능)      

- [개발 완료] AOT(Ahead-Of-Time) 컴파일러로 빌드   
 앱 배포 시, AOT 컴파일러를 통해 미리 변환한 소스 코드를 적용하고자 하는 CPU 아키텍쳐에 맞는 기계어로 변환시켜줌.    

 ### 2. null safety   

 ---
 Why flutter chooses dart?
 ===   

 ### 1. JIT, AOT 컴파일러 둘 다 존재하기 때문.
 ### 2. 둘 다 구글이 만들었기 때문.

