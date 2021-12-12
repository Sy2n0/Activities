## Buffer Overflow

##### 작성자 : 양지용
##### 소속 : Anti-root

<hr>

## 참고 내용 및 공부 URL
[2premise 버퍼오버 플로우란?, 버퍼오버 플로우 예방책](https://je0n-je.tistory.com/12) <br>
[IT_Try 메모리 구조](https://cwjuns.tistory.com/17) <br>
[D4m0n Buffer Overflow 기초](https://d4m0n.tistory.com/14)

<hr>

## 목차
* 1. What is Buffer Overflow ?
* 2. Buffer Overflow 종류
* 3. Buffer Overflow 실습
* 4. Buffer Overflow 예방책

<hr>

## 1. What is Buffer Overflow ?
Buffer Overflow 는 C 언어에서 버퍼에 데이터를 입력받을 때 입력 값에 크기를 검증하지 않아 버퍼가 일정량을 넘어서서 메모리나 변수들을 덮어 씌우게되는 버그이다.
이러한 취약점은 Return Address를 원하는 주소로 덮어 씌우고 Instruction Pointer를 제어할 수 있다.

좀 더 쉽게 이야기를 하자면 넘칠때까지 물을 받아놓은 컵에 물을 더 부어서 물이 넘치는 것과 같은 행위인것이다.

<hr>

## 2. Buffer Overflow 종류
총 2가지에 Buffer Overflow가 있다.
* 1. Stack Buffer Overflow
* 2. Heap Buffer Overflow


### 2-1. What is Stack Buffer Overflow ?
Stack Buffer Overflow 에 정확한 개념을 알기 전 Stack에 대해서 먼저 알아보자.
> What is Stack ?

```함수를 호출 할 때 사용되는 지역 변수, 매개 변수, 리턴 값 등의 임시 데이터를 저장하는 영역 (LIFO 방식 [후입선출 방식])```

이렇게 간단하게 Stack에 대해서 알아봤는데 이제 처음에 알아본 Buffer Overflow와 Stack에 개념을 합치면 된다.

Stack Buffer Overflow란 스택에 할당된 버퍼들이 문자열 계산 등에 의해 미리 정의된 버퍼의 크기를 넘는 경우에 발생한다.

### 2-2. What is Heap Buffer Overflow ?
Heap Buffer Overflow 또한 정확한 개념을 알기 전 Heap에 대해서 먼저 알아보자.
> What is Heap ?

```프로그래머가 동적 할당/해제하는 메모리 공간이며 메모리에 낮은 주소에서 높은 주소의 방향으로 할당된다. ```

이렇게 또 새롭게 Heap에 대해서 알아봤으니 Stack과 같이 Buffer Overflow 개념을 합치면 된다.

Heap Buffer Overflow란 힙에 할당된 버퍼들에 문자열 등이 저장되어질 때 사용자가 미리 정의한 크기의 힙 메모리 사이즈를 초과하여 문자열 등이 저장되어 질 경우에 발생한다.

<hr>

## 3. Buffer Overflow 실습

먼저 BOF 실습을 위해서 총 2가지에 코드를 준비해보았다.
* 1. Stack Buffer Overflow
* 2. Heap Buffer Overflow

먼저 Stack BOF에 버그 파일을 준비해보았습니다.
```
#include<stdio.h>

#include<string.h>
 
int main(int argc, char *argv[])

{

 char buffer[8];

 strcpy(buffer,argv[1]);

printf("%s\n",&buffer);

return 0;

}
````

<img width="1122" alt="Screen Shot 2021-12-12 at 9 42 57 PM" src="https://user-images.githubusercontent.com/84657474/145712725-e0554677-8b5e-40f2-bce9-b00260d76b6f.png">

컴파일 후 파일을 실행시켜 확인해보았다.
