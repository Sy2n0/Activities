# x86 Assembly๐ค: Essential Part(1)
์์ฑ์ : Syno

<hr>

### Introduction(์๋ก )     
1. Hook     
์ฌ์ค ์ฒ์ ์ฃผ์ ๋ฅผ ์ก์๊ฒ์ ```cve-2016-0728``` ์ด์๋๋ฐ.. ๋๋ฌด ๋ง์ ๊ณณ์์ ๋งํ๊ณ  ํผ์ ์คํธ๋ ์ค ๋ฐ๊ณ ์์ด์ ์ฃผ์ ๋ฅผ ๊ฐ์ํ๊ฑด ๋น๋ฐ..     
๊ณต๋ถ๋ฅผ ์ด๋ฏธ ์งํํ ๋ถ๋ถ์ด์ง๋ง ๋ค์ ํ๋ฒ ๋ณต์ตํ๋ค๋ ๋ง์ธ๋๋ก ์ฃผ์ ๋ฅผ ์ ์ ํ์ด๋๋ค.     
https://dreamhack.io/lecture/courses/37

2. General Statement
- Assembly Language
- ์ด์๋ธ๋ฆฌ์ด์ x86-64
- x86-64 ์ด์๋ธ๋ฆฌ ๋ช๋ น์ด
	
<hr>

### Body(๋ณธ๋ก )
#### 1. Assembly Language
์ด์๋ธ๋ฆฌ ์ธ์ด๋ ์ปดํจํฐ์ ๊ธฐ๊ณ์ด์ ์นํ๋๋ ์ธ์ด์๋๋ค.    
- ๊ธฐ๊ณ์ด๊ฐ ์ฌ๋ฌ ์ข๋ฅ๋ผ๋ฉด ์ด์๋ธ๋ฆฌ์ด ๋ํ ์ฌ๋ฌ ์ข๋ฅ์ฌ์ผํ๋ค.

CPU์ ์ฌ์ฉ๋๋ ISA ์ข๋ฅ
- IA-32, x86-64, ARM, MIPS ๋ฑ ์ข๋ฅ๊ฐ ๊ต์ฅํ ๋ค์ํ๋ค.

์ฝ๊ฒ x64๋ x64๋ง์ ์ด์๋ธ๋ฆฌ์ด๊ฐ ์๊ณ , ARM์ด๋ฉด ARM๋ง์ ์ด์๋ธ๋ฆฌ๊ฐ ์กด์ฌํ๋ ๊ฒ์ด๋ค.

#### 2. ์ด์๋ธ๋ฆฌ์ด์ x86-64

- 2-1 ๊ธฐ๋ณธ ๊ตฌ์กฐ
	- ํ๊ตญ์ด : ์ฃผ์ด, ๋ชฉ์ ์ด, ์์ ์ด ๋ฑ์ผ๋ก ๊ตฌ์ฑ 
	- ์ด์๋ธ๋ฆฌ์ด : ๋์ฌ์ ํด๋นํ๋ **๋ช๋ น์ด(Opcode)**, ๋ชฉ์ ์ด์ ํด๋นํ๋ **ํผ์ฐ์ฐ์(Operand)** ๋ก ๊ตฌ์ฑ 

- 2-2 ๋ช๋ น์ด
	- ์ธํ์ x64์๋ ๋ช๋ น์ด๊ฐ ๊ต์ฅํ ๋ง๋ค.
	<img width="700" alt="Screen Shot 2022-01-08 at 8 47 08 PM" src="https://user-images.githubusercontent.com/84657474/148642938-22efde76-6b1c-4982-9b52-f64a6bc7079d.png">
		
- 2-3 ํผ์ฐ์ฐ์
	- ํผ์ฐ์ฐ์์๋ 3๊ฐ์ง์ ์ข๋ฅ๊ฐ ์ฌ ์ ์๋ค.
		- ์์ (Immediate Value)
		- ๋ ์ง์คํฐ (Register)
		- ๋ฉ๋ชจ๋ฆฌ (Memory)

	- ๋ฉ๋ชจ๋ฆฌ ํผ์ฐ์ฐ์๋ **[]** ์ผ๋ก ๋๋ฌ์ธ์ธ ๊ฒ์ผ๋ก ํํ์ด ๋๋ฉฐ, ์์๋ ํฌ๊ธฐ ์ง์ ์์ธ TYPE PTR์ ํฌํจ์ํฌ ์ ์๋ค.
	- TYPE์๋ BYTE / WORD / DWORD / QWORD๊ฐ ์ฌ ์ ์์ผ๋ฉฐ, ์์๋๋ก 1byte, 2byte, 4byte, 8byte์ ํฌ๊ธฐ๋ฅผ ์ง์ ํ๋ค.

#### 3. x86-64 ์ด์๋ธ๋ฆฌ ๋ช๋ น์ด

- 4-1 ๋ฐ์ดํฐ ์ด๋
	- ์ด๋ ํ ๊ฐ์ ๋ฉ๋ชจ๋ฆฌ๋ ๋ ์ง์คํฐ๋ก ์ฎ๊ธฐ๋๋ก ์ง์ํ๋ค.
	- ``` ex) mov rdi, rsi -> rsi์ ๊ฐ์ rdi์ ๋์ ```
	- ``` ex) lea rsi, [rbx+8*rcx] -> rbx+8*rcx ๋ฅผ rsi์ ๋์ ```
	
- 4-2 ์ฐ์  ์ฐ์ฐ
	- ๋ง์, ๋บ์, ๊ณฑ์, ๋๋์ ์ฐ์ฐ์ ์ง์ํ๋ค.
	- ``` ex) add eax, 3 -> eax += 3 ```
	- ``` ex) sub eax, 3 -> eax -= 3 ```
	- ``` ex) inc eax -> eax += 1 ```
	- ``` ex) dec eax -> eax -= 1 ```

- 4-3 ๋ผ๋ฆฌ ์ฐ์ฐ(and, or)
	- and, or, xor, neg๋ฑ์ ๋นํธ ์ฐ์ฐ์ ์ง์ํ๋ค.
		<img width="698" alt="Screen Shot 2022-01-08 at 9 10 01 PM" src="https://user-images.githubusercontent.com/84657474/148643630-ee2f550c-c26b-4028-b668-57948e140b61.png">
		<img width="698" alt="Screen Shot 2022-01-08 at 9 10 15 PM" src="https://user-images.githubusercontent.com/84657474/148643637-23453b1b-e08e-4c40-9b17-6ceb4a6fbe07.png">
		<img width="1191" alt="Screen Shot 2022-01-08 at 9 14 02 PM" src="https://user-images.githubusercontent.com/84657474/148643744-e5fd6ff3-1f5f-481b-8f98-ae18236eae58.png">
		
- 4-4 ๋ผ๋ฆฌ ์ฐ์ฐ(xor, not)

	<img width="699" alt="Screen Shot 2022-01-08 at 9 15 08 PM" src="https://user-images.githubusercontent.com/84657474/148643777-ccfc3935-782e-4bba-b912-d80acac053f4.png">
	<img width="699" alt="Screen Shot 2022-01-08 at 9 15 28 PM" src="https://user-images.githubusercontent.com/84657474/148643786-da786358-20e1-4544-885b-8d315767c24b.png">
	<img width="1473" alt="Screen Shot 2022-01-08 at 9 20 10 PM" src="https://user-images.githubusercontent.com/84657474/148643890-e5a498c4-6abd-4f22-be52-7beeaeda22cd.png">

- 4-5 ๋น๊ต
	- ๋ ํผ์ฐ์ฐ์์ ๊ฐ์ ๋น๊ตํ๊ณ , ํ๋๊ทธ๋ฅผ ์ค์ ํ๋ค.
		<img width="697" alt="Screen Shot 2022-01-08 at 9 23 59 PM" src="https://user-images.githubusercontent.com/84657474/148643992-f9d30ea2-ec64-4c58-9625-5c5b43e5055e.png">
		<img width="697" alt="Screen Shot 2022-01-08 at 9 24 20 PM" src="https://user-images.githubusercontent.com/84657474/148644004-4cce9bca-0e9e-49ce-8875-6a0a1fa1643e.png">

- 4-6 ๋ถ๊ธฐ
	- rip๋ฅผ ์ด๋์์ผ ์คํ ํ๋ฆ์ ๋ฐ๊พผ๋ค.
	
		<img width="699" alt="Screen Shot 2022-01-08 at 9 27 35 PM" src="https://user-images.githubusercontent.com/84657474/148644107-d4d5850f-565e-4ece-8646-07a813e1205e.png">
		<img width="697" alt="Screen Shot 2022-01-08 at 9 27 44 PM" src="https://user-images.githubusercontent.com/84657474/148644111-8804d8f3-bcc2-4484-90d3-75980c16723c.png">
		<img width="699" alt="Screen Shot 2022-01-08 at 9 27 54 PM" src="https://user-images.githubusercontent.com/84657474/148644120-8162b820-3bf9-4514-94d8-504597c400c2.png">


<hr>

### Conclusion(๊ฒฐ๋ก )

1. ๋ฐ์ดํฐ ์ด๋ ์ฐ์ฐ์
	- mov dst, src: src์ ๊ฐ์ dst์ ๋์
	- lea dst, src: src์ ์ ํจ ์ฃผ์๋ฅผ dst์ ๋์

2. ์ฐ์  ์ฐ์ฐ
	- add dst, src: src์ ๊ฐ์ dst์ ๋ํ๋ค.
	- sub dst, src: src์ ๊ฐ์ dst์์ ๋บ๋ค.
	- inc op: op์ ๊ฐ์ 1 ๋ํ๋ค.
	- dec op: op์ ๊ฐ์ 1 ๋บ๋ค.

3. ๋ผ๋ฆฌ ์ฐ์ฐ
	- and dst, src: dst์ src๊ฐ ๋ชจ๋ 1์ด๋ฉด 1, ์๋๋ฉด 0
	- or dst, src: dst์ src์ค ํ ์ชฝ์ด๋ผ๋ 1์ด๋ฉด 1, ์๋๋ฉด 0
	- xor dst, src: dst์ src๊ฐ ๋ค๋ฅด๋ฉด 1, ๊ฐ์ผ๋ฉด 0
	- not op: op์ ๋นํธ๋ฅผ ๋ชจ๋ ๋ฐ์ 
4. ๋น๊ต
	- cmp op1, op2: op1์์ op2๋ฅผ ๋นผ๊ณ  ํ๋๊ทธ๋ฅผ ์ค์ ํ๋ค.
	- test op1, op2: op1๊ณผ op2์ AND ์ฐ์ฐ์ ํ๊ณ , ํ๋๊ทธ๋ฅผ ์ค์ ํ๋ค.

5. ๋ถ๊ธฐ
	- jmp addr: addr๋ก rip ์ด๋ํ๋ค.
	- je addr: ์ง์  ๋น๊ต์์ ๋ ํผ์ฐ์ฐ์์ ๊ฐ์ด ๊ฐ์ ๊ฒฝ์ฐ addr๋ก rip ์ด๋ํ๋ค.
	- jg addr: ์ง์  ๋น๊ต์์ ๋ ํผ์ฐ์ฐ์ ์ค ์ ์์ ๊ฐ์ด ๋ ํด ๊ฒฝ์ฐ addr๋ก rip ์ด๋ํ๋ค.
