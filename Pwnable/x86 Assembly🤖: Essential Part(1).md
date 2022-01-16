# x86 Assembly🤖: Essential Part(1)
작성자 : Syno

<hr>

### Introduction(서론)     
1. Hook     
사실 처음 주제를 잡은것은 ```cve-2016-0728``` 이였는데.. 너무 많은 곳에서 막히고 혼자 스트레스 받고있어서 주제를 갈아탄건 비밀..     
공부를 이미 진행한 부분이지만 다시 한번 복습한다는 마인드로 주제를 선정했슴니다.     
https://dreamhack.io/lecture/courses/37

2. General Statement
- Assembly Language
- 어셈블리어와 x86-64
- x86-64 어셈블리 명령어
	
<hr>

### Body(본론)
#### 1. Assembly Language
어셈블리 언어는 컴퓨터의 기계어와 치환되는 언어입니다.    
- 기계어가 여러 종류라면 어셈블리어 또한 여러 종류여야한다.

CPU에 사용되는 ISA 종류
- IA-32, x86-64, ARM, MIPS 등 종류가 굉장히 다양하다.

쉽게 x64는 x64만에 어셈블리어가 있고, ARM이면 ARM만에 어셈블리가 존재하는 것이다.

#### 2. 어셈블리어와 x86-64

- 2-1 기본 구조
	- 한국어 : 주어, 목적어, 서술어 등으로 구성 
	- 어셈블리어 : 동사에 해당하는 **명령어(Opcode)**, 목적어에 해당하는 **피연산자(Operand)** 로 구성 

- 2-2 명령어
	- 인텔의 x64에는 명령어가 굉장히 많다.
	<img width="700" alt="Screen Shot 2022-01-08 at 8 47 08 PM" src="https://user-images.githubusercontent.com/84657474/148642938-22efde76-6b1c-4982-9b52-f64a6bc7079d.png">
		
- 2-3 피연산자
	- 피연산자에는 3가지에 종류가 올 수 있다.
		- 상수 (Immediate Value)
		- 레지스터 (Register)
		- 메모리 (Memory)

	- 메모리 피연산자는 **[]** 으로 둘러싸인 것으로 표현이 되며, 앞에는 크기 지정자인 TYPE PTR을 포함시킬 수 있다.
	- TYPE에는 BYTE / WORD / DWORD / QWORD가 올 수 있으며, 순서대로 1byte, 2byte, 4byte, 8byte의 크기를 지정한다.

#### 3. x86-64 어셈블리 명령어

- 4-1 데이터 이동
	- 어떠한 값을 메모리나 레지스터로 옮기도록 지시한다.
	- ``` ex) mov rdi, rsi -> rsi의 값을 rdi에 대입 ```
	- ``` ex) lea rsi, [rbx+8*rcx] -> rbx+8*rcx 를 rsi에 대입 ```
	
- 4-2 산술 연산
	- 덧셈, 뺄셈, 곱셈, 나눗셈 연산을 지시한다.
	- ``` ex) add eax, 3 -> eax += 3 ```
	- ``` ex) sub eax, 3 -> eax -= 3 ```
	- ``` ex) inc eax -> eax += 1 ```
	- ``` ex) dec eax -> eax -= 1 ```

- 4-3 논리 연산(and, or)
	- and, or, xor, neg등에 비트 연산을 지시한다.
		<img width="698" alt="Screen Shot 2022-01-08 at 9 10 01 PM" src="https://user-images.githubusercontent.com/84657474/148643630-ee2f550c-c26b-4028-b668-57948e140b61.png">
		<img width="698" alt="Screen Shot 2022-01-08 at 9 10 15 PM" src="https://user-images.githubusercontent.com/84657474/148643637-23453b1b-e08e-4c40-9b17-6ceb4a6fbe07.png">
		<img width="1191" alt="Screen Shot 2022-01-08 at 9 14 02 PM" src="https://user-images.githubusercontent.com/84657474/148643744-e5fd6ff3-1f5f-481b-8f98-ae18236eae58.png">
		
- 4-4 논리 연산(xor, not)

	<img width="699" alt="Screen Shot 2022-01-08 at 9 15 08 PM" src="https://user-images.githubusercontent.com/84657474/148643777-ccfc3935-782e-4bba-b912-d80acac053f4.png">
	<img width="699" alt="Screen Shot 2022-01-08 at 9 15 28 PM" src="https://user-images.githubusercontent.com/84657474/148643786-da786358-20e1-4544-885b-8d315767c24b.png">
	<img width="1473" alt="Screen Shot 2022-01-08 at 9 20 10 PM" src="https://user-images.githubusercontent.com/84657474/148643890-e5a498c4-6abd-4f22-be52-7beeaeda22cd.png">

- 4-5 비교
	- 두 피연산자의 값을 비교하고, 플래그를 설정한다.
		<img width="697" alt="Screen Shot 2022-01-08 at 9 23 59 PM" src="https://user-images.githubusercontent.com/84657474/148643992-f9d30ea2-ec64-4c58-9625-5c5b43e5055e.png">
		<img width="697" alt="Screen Shot 2022-01-08 at 9 24 20 PM" src="https://user-images.githubusercontent.com/84657474/148644004-4cce9bca-0e9e-49ce-8875-6a0a1fa1643e.png">

- 4-6 분기
	- rip를 이동시켜 실행 흐름을 바꾼다.
	
		<img width="699" alt="Screen Shot 2022-01-08 at 9 27 35 PM" src="https://user-images.githubusercontent.com/84657474/148644107-d4d5850f-565e-4ece-8646-07a813e1205e.png">
		<img width="697" alt="Screen Shot 2022-01-08 at 9 27 44 PM" src="https://user-images.githubusercontent.com/84657474/148644111-8804d8f3-bcc2-4484-90d3-75980c16723c.png">
		<img width="699" alt="Screen Shot 2022-01-08 at 9 27 54 PM" src="https://user-images.githubusercontent.com/84657474/148644120-8162b820-3bf9-4514-94d8-504597c400c2.png">


<hr>

### Conclusion(결론)

1. 데이터 이동 연산자
	- mov dst, src: src의 값을 dst에 대입
	- lea dst, src: src의 유효 주소를 dst에 대입

2. 산술 연산
	- add dst, src: src의 값을 dst에 더한다.
	- sub dst, src: src의 값을 dst에서 뺀다.
	- inc op: op의 값을 1 더한다.
	- dec op: op의 값을 1 뺀다.

3. 논리 연산
	- and dst, src: dst와 src가 모두 1이면 1, 아니면 0
	- or dst, src: dst와 src중 한 쪽이라도 1이면 1, 아니면 0
	- xor dst, src: dst와 src가 다르면 1, 같으면 0
	- not op: op의 비트를 모두 반전
4. 비교
	- cmp op1, op2: op1에서 op2를 빼고 플래그를 설정한다.
	- test op1, op2: op1과 op2에 AND 연산을 하고, 플래그를 설정한다.

5. 분기
	- jmp addr: addr로 rip 이동한다.
	- je addr: 직전 비교에서 두 피연산자의 값이 같을 경우 addr로 rip 이동한다.
	- jg addr: 직전 비교에서 두 피연산자 중 전자의 값이 더 클 경우 addr로 rip 이동한다.
