# NFA
## 使用 Thompson 构造法为下列正规式构造 NFA，写出每个 NFA 处理符号串“𝑎𝑏𝑎𝑏𝑏𝑎𝑏”过程中的状态转换序列
### (a|b)*
![image](https://user-images.githubusercontent.com/49871906/229751826-c2bbb71f-5657-483d-80a6-e55f53bc646c.png)  
0-1-2-3-6-1-4-5-6-1-2-3-6-1-4-5-6-1-4-5-6-1-2-3-6-1-4-5-6-7  
### (a*|b*)*
![image](https://user-images.githubusercontent.com/49871906/229752101-710f4754-093a-41e9-9f80-a3fe00d350cd.png)  
0-1-2-3-4-5-10-1-6-7-8-9-10-1-2-3-4-5-10-1-6-7-8-7-8-9-10-1-2-3-4-5-10-1-6-7-8-9-10-11  
### ((ϵ |a)b*)*
![image](https://user-images.githubusercontent.com/49871906/229752150-eaa26503-3c31-44d5-8af3-350aa32febd9.png)  
0-1-2-3-6-7-8-9-1-2-3-6-7-8-7-8-9-1-2-3-6-7-8-9-10  
0-1-2-3-6-7-8-9-1-2-3-6-7-8-9-1-4-5-6-7-8-9-1-2-3-6-7-8-9-10  
### (a|b)\*abb(a|b)\*
![image](https://user-images.githubusercontent.com/49871906/229752259-92158c62-565b-45b8-97aa-e2636c3b1b54.png)  
0-1-2-3-6-1-4-5-6-7-8-9-10-11-12-13-16-11-14-15-16-17  
## 利用子集构造法将第一题得到的 NFA 转换为 DFA，同样写出分析符号串“𝑎𝑏𝑎𝑏𝑏𝑎𝑏”过程中的状态转换
### (a|b)*
NFA初始状态为状态0，A={0, 1, 2, 4, 7}  
- A被加上标记，对于输入符号a,b,有
  - B = Dtrans\[A,a\] = ϵ-closure(move(A,a)) = ϵ-closure({3}) = {1, 2, 3, 4, 6, 7}
  - C = Dtrans\[A,b\] = ϵ-closure(move(A,b)) = ϵ-closure({5}) = {1, 2, 4, 5, 6, 7}
- B被加上标记，对于输入符号a,b,有:
  - B = Dtrans\[B,a\] = ϵ-closure(move(B,a)) = ϵ-closure({3}) = {1, 2, 3, 4, 6, 7}
  - C = Dtrans\[B,b\] = ϵ-closure(move(B,b)) = ϵ-closure({5}) = {1, 2, 4, 5, 6, 7}
- C被加上标记，对于输入符号a,b,有:
  - B = Dtrans\[C,a\] = ϵ-closure(move(C,a)) = ϵ-closure({3}) = {1, 2, 3, 4, 6, 7}
  - C = Dtrans\[C,b\] = ϵ-closure(move(C,b)) = ϵ-closure({5}) = {1, 2, 4, 5, 6, 7}  

|NFA状态|DFA状态|a|b|
|-|-|-|-|
|{0, 1, 2, 4, 7}|A|B|C|
|{1, 2, 3, 4, 6, 7}|B|B|C|
|{1, 2, 4, 5, 6, 7}|C|B|C|

![image](https://user-images.githubusercontent.com/49871906/229771241-a82e3846-29c1-4585-9694-38cdd7bc9aab.png)  

状态转移：0-1-2-1-2-2-1-2
### (a*|b*)*
NFA初始状态为状态0，A={0, 1, 2, 3, 5, 6, 7, 9, 10, 11}  
- A被加上标记，对于输入符号a,b,有:  
  - B = Dtrans\[A,a\] = ϵ-closure(move(A,a)) = ϵ-closure({4}) = {1, 2, 3, 4, 5, 6, 7, 9, 10, 11}
  - C = Dtrans\[A,b\] = ϵ-closure(move(A,b)) = ϵ-closure({8}) = {1, 2, 3, 5, 6, 7, 8, 9, 10, 11}
- B被加上标记，对于输入符号a,b,有:
  - B = Dtrans\[B,a\] = ϵ-closure(move(B,a)) = ϵ-closure({4}) = {1, 2, 3, 4, 5, 6, 7, 9, 10, 11}
  - C = Dtrans\[B,b\] = ϵ-closure(move(B,b)) = ϵ-closure({8}) = {1, 2, 3, 5, 6, 7, 8, 9, 10, 11}
- C被加上标记，对于输入符号a,b,有:
  - B = Dtrans\[C,a\] = ϵ-closure(move(C,a)) = ϵ-closure({4}) = {1, 2, 3, 4, 5, 6, 7, 9, 10, 11}
  - C = Dtrans\[C,b\] = ϵ-closure(move(C,b)) = ϵ-closure({8}) = {1, 2, 3, 5, 6, 7, 8, 9, 10, 11}  

|NFA状态|DFA状态|a|b|
|-|-|-|-|
|{0, 1, 2, 3, 5, 6, 7, 9, 10, 11}|A|B|C|
|{1, 2, 3, 4, 5, 6, 7, 9, 10, 11}|B|B|C|
|{1, 2, 3, 5, 6, 7, 8, 9, 10, 11}|C|B|C|

![image](https://user-images.githubusercontent.com/49871906/229771242-3f98a829-364f-467b-ba90-827bbc339f09.png)

状态转移：0-1-2-1-2-2-1-2
### ((ϵ |a)b*)*
NFA初始状态为状态0，A={0, 1, 2, 4, 5, 6, 7, 9, 10}  
- A被加上标记，对于输入符号a,b,有:  
  - B = Dtrans\[A,a\] = ϵ-closure(move(A,a)) = ϵ-closure({3}) = {1, 2, 3, 4, 5, 6, 7, 9, 10}
  - C = Dtrans\[A,b\] = ϵ-closure(move(A,b)) = ϵ-closure({8}) = {1, 2, 4, 5, 6, 7, 8, 9, 10}
- B被加上标记，对于输入符号a,b,有:
  - B = Dtrans\[B,a\] = ϵ-closure(move(B,a)) = ϵ-closure({3}) = {1, 2, 3, 4, 5, 6, 7, 9, 10}
  - C = Dtrans\[B,b\] = ϵ-closure(move(B,b)) = ϵ-closure({8}) = {1, 2, 4, 5, 6, 7, 8, 9, 10}
- C被加上标记，对于输入符号a,b,有:
  - B = Dtrans\[C,a\] = ϵ-closure(move(C,a)) = ϵ-closure({3}) = {1, 2, 3, 4, 5, 6, 7, 9, 10}
  - C = Dtrans\[C,b\] = ϵ-closure(move(C,b)) = ϵ-closure({8}) = {1, 2, 4, 5, 6, 7, 8, 9, 10}  

|NFA状态|DFA状态|a|b|
|-|-|-|-|
|{0, 1, 2, 4, 5, 6, 7, 9, 10}|A|B|C|
|{1, 2, 3, 4, 5, 6, 7, 9, 10}|B|B|C|
|{1, 2, 4, 5, 6, 7, 8, 9, 10}|C|B|C|

![image](https://user-images.githubusercontent.com/49871906/229771312-aa1f4d83-22f5-4f79-9d9d-5f2785f70993.png)

状态转移：0-1-2-1-2-2-1-2
### (a|b)\*abb(a|b)\*
NFA初始状态为状态0，A={0, 1, 2, 4, 7}  
- A被加上标记，对于输入符号a,b,有:  
  - B = Dtrans\[A,a\] = ϵ-closure(move(A,a)) = ϵ-closure({3, 8}) = {1, 2, 3, 4, 6, 7, 8}
  - C = Dtrans\[A,b\] = ϵ-closure(move(A,b)) = ϵ-closure({5}) = {1, 2, 4, 5, 6, 7}
- B被加上标记，对于输入符号a,b,有:
  - B = Dtrans\[B,a\] = ϵ-closure(move(B,a)) = ϵ-closure({3, 8}) = {1, 2, 3, 4, 6, 7, 8}
  - D = Dtrans\[B,b\] = ϵ-closure(move(B,b)) = ϵ-closure({5, 9}) = {1, 2, 4, 5, 6, 7, 9}
- C被加上标记，对于输入符号a,b,有:
  - B = Dtrans\[C,a\] = ϵ-closure(move(C,a)) = ϵ-closure({3, 8}) = {1, 2, 3, 4, 6, 7, 8}
  - C = Dtrans\[C,b\] = ϵ-closure(move(C,b)) = ϵ-closure({5}) = {1, 2, 4, 5, 6, 7}
- D被加上标记，对于输入符号a,b,有:
  - B = Dtrans\[D,a\] = ϵ-closure(move(D,a)) = ϵ-closure({3, 8}) = {1, 2, 3, 4, 6, 7, 8}
  - E = Dtrans\[D,b\] = ϵ-closure(move(D,b)) = ϵ-closure({5, 10}) = {1, 2, 4, 5, 6, 7, 10, 11, 12, 14, 17}
- E被加上标记，对于输入符号a,b,有:
  - F = Dtrans\[E,a\] = ϵ-closure(move(E,a)) = ϵ-closure({3, 8, 13}) = {1, 2, 3, 4, 6, 7, 8, 11, 12, 13, 14, 16, 17}
  - G = Dtrans\[E,b\] = ϵ-closure(move(E,b)) = ϵ-closure({5, 15}) = {1, 2, 4, 5, 6, 7, 11, 12, 14, 15, 16, 17}
- F被加上标记，对于输入符号a,b,有:
  - F = Dtrans\[F,a\] = ϵ-closure(move(F,a)) = ϵ-closure({3, 8, 13}) = {1, 2, 3, 4, 6, 7, 8, 11, 12, 13, 14, 16, 17}
  - H = Dtrans\[F,b\] = ϵ-closure(move(F,b)) = ϵ-closure({5, 9, 15}) = {1, 2, 4, 5, 6, 7, 9, 11, 12, 14, 15, 16, 17}
- G被加上标记，对于输入符号a,b,有:
  - F = Dtrans\[G,a\] = ϵ-closure(move(G,a)) = ϵ-closure({3, 8, 13}) = {1, 2, 3, 4, 6, 7, 8, 11, 12, 13, 14, 16, 17}
  - G = Dtrans\[G,b\] = ϵ-closure(move(G,b)) = ϵ-closure({5, 15}) = {1, 2, 4, 5, 6, 7, 11, 12, 14, 15, 16, 17}
- H被加上标记，对于输入符号a,b,有:
  - F = Dtrans\[H,a\] = ϵ-closure(move(H,a)) = ϵ-closure({3, 8, 13}) = {1, 2, 3, 4, 6, 7, 8, 11, 12, 13, 14, 16, 17}
  - I = Dtrans\[H,b\] = ϵ-closure(move(H,b)) = ϵ-closure({5, 10, 15}) = {1, 2, 4, 5, 6, 7, 10, 11, 12, 14, 15, 16, 17}
- I被加上标记，对于输入符号a,b,有:
  - F = Dtrans\[I,a\] = ϵ-closure(move(I,a)) = ϵ-closure({3, 8, 13}) = {1, 2, 3, 4, 6, 7, 8, 11, 12, 13, 14, 16, 17}
  - G = Dtrans\[I,b\] = ϵ-closure(move(I,b)) = ϵ-closure({5, 15}) = {1, 2, 4, 5, 6, 7, 11, 12, 14, 15, 16, 17}

|NFA状态|DFA状态|a|b|
|-|-|-|-|
|{0, 1, 2, 4, 7}|A|B|C|
|{1, 2, 3, 4, 6, 7, 8}|B|B|D|
|{1, 2, 4, 5, 6, 7}|C|B|C|
|{1, 2, 4, 5, 6, 7, 9}|D|B|E|
|{1, 2, 4, 5, 6, 7, 10, 11, 12, 14, 17}|E|F|G|
|{1, 2, 3, 4, 6, 7, 8, 11, 12, 13, 14, 16, 17}|F|F|H|
|{1, 2, 4, 5, 6, 7, 11, 12, 14, 15, 16, 17}|G|F|G|
|{1, 2, 4, 5, 6, 7, 9, 11, 12, 14, 15, 16, 17}|H|F|I|
|{1, 2, 4, 5, 6, 7, 10, 11, 12, 14, 15, 16, 17}|I|F|G|

![image](https://user-images.githubusercontent.com/49871906/229772199-361dbeed-1e6b-483d-b3ee-337b6e976d85.png)

状态转移：0-1-3-1-3-4-5-7

# DFA
## 直接构造法构造这四个正则表达式的DFA，并且最小化DFA
### (a|b)*
![image](https://user-images.githubusercontent.com/49871906/231948699-15a0e8b9-cc4f-48d1-be5b-f26f6a65e07f.png)
|节点|followpos|
|-|-|
|1|{1,2,3}|
|2|{1,2,3}|
|3|{}|

初始状态A = firstpos(root) = {1,2,3}  
- A被加上标记，对于输入符号a,b,有:  
  - A = Dtrans\[A,a\] = {1,2,3}
  - A = Dtrans\[A,b\] = {1,2,3}
 
![image](https://user-images.githubusercontent.com/49871906/231993325-ed3d2bf2-637e-4121-bb19-2e9fe0454041.png)

只有一个状态，已经是最小化
### (a*|b*)*
![image](https://user-images.githubusercontent.com/49871906/231948720-4d495e30-8f27-4022-b037-50fa85eccd42.png)
|节点|followpos|
|-|-|
|1|{1,2,3}|
|2|{1,2,3}|
|3|{}|

初始状态A = firstpos(root) = {1,2,3}  
- A被加上标记，对于输入符号a,b,有:  
  - A = Dtrans\[A,a\] = {1,2,3}
  - A = Dtrans\[A,b\] = {1,2,3}
 
![image](https://user-images.githubusercontent.com/49871906/231993343-332d5def-22b3-4baa-b22e-913386c034f7.png)

只有一个状态，已经是最小化
### ((ϵ |a)b*)*
![image](https://user-images.githubusercontent.com/49871906/231952501-81448778-5b8b-4283-96ca-207d9ea527a6.png)
|节点|followpos|
|-|-|
|1|{1,2,3}|
|2|{1,2,3}|
|3|{}|

初始状态A = firstpos(root) = {1,2,3}  
- A被加上标记，对于输入符号a,b,有:  
  - A = Dtrans\[A,a\] = {1,2,3}
  - A = Dtrans\[A,b\] = {1,2,3}
 
![image](https://user-images.githubusercontent.com/49871906/231993304-c237c965-c3ed-4cdd-b673-44fb8c129c00.png)

只有一个状态，已经是最小化
### (a|b)\*abb(a|b)\*
![image](https://user-images.githubusercontent.com/49871906/231952520-0d5ecb83-eac5-4482-9165-c22c2e3b6237.png)
|节点|followpos|
|-|-|
|1|{1,2,3}|
|2|{1,2,3}|
|3|{4}|
|4|{5}|
|5|{6,7,8}|
|6|{6,7,8}|
|7|{6,7,8}|
|8|{}|

初始状态A = firstpos(root) = {1,2,3}  
- A被加上标记，对于输入符号a,b,有:  
  - B = Dtrans\[A,a\] = {1,2,3,4}
  - A = Dtrans\[A,b\] = {1,2,3}
- B被加上标记，对于输入符号a,b,有:  
  - B = Dtrans\[B,a\] = {1,2,3,4}
  - C = Dtrans\[B,b\] = {1,2,3,5}
- C被加上标记，对于输入符号a,b,有:  
  - B = Dtrans\[C,a\] = {1,2,3,4}
  - D = Dtrans\[C,b\] = {1,2,3,6,7,8}
- D被加上标记，对于输入符号a,b,有:  
  - E = Dtrans\[D,a\] = {1,2,3,4,6,7,8}
  - D = Dtrans\[D,b\] = {1,2,3,6,7,8}
- E被加上标记，对于输入符号a,b,有:  
  - E = Dtrans\[E,a\] = {1,2,3,4,6,7,8}
  - F = Dtrans\[E,b\] = {1,2,3,5,6,7,8}
- F被加上标记，对于输入符号a,b,有:  
  - E = Dtrans\[F,a\] = {1,2,3,4,6,7,8}
  - D = Dtrans\[F,b\] = {1,2,3,6,7,8}

![image](https://user-images.githubusercontent.com/49871906/231998839-c67f3ea3-4dac-4453-a3e0-7105ce249e05.png)

最小化：  
- {0,1,2} {3,4,5} =>
- {0,1} {2} {3,4,5} =>
- {0} {1} {2} {3,4,5}

![image](https://user-images.githubusercontent.com/49871906/232007311-0c4fe065-8007-4e29-bab2-fc5b849ff6f9.png)

# CFG
## 为下列语言设计上下文无关文法。也请思考下列语言可不可以设计正规表达式?
### 满足这样条件的二进制串:每个 0 之后都紧跟着至少一个 1
S ->1S|0A|ε  
A ->1S  
正规式：(1*01)*  
### 0 和 1 个数相等的二进制串
S ->S0S1S|S1S0S|ε  
无正规式  
### 不含 011 子串的二进制串
S ->1S|0A|ε  
A ->0A|1B|ε  
B ->0A|ε  
正规式：1*(0|01)*  
### 具有形式𝑥𝑦的二进制串，x ≠ y
S -> AB|BA  
A ->CAC|0  
B ->CBC|1  
C ->0|1|ε  
无正规式  
### 形如𝑥𝑥的二进制串
S -> AA  
A -> A1|A0|ε  
无正规式  
##  考虑文法
𝑆 → (𝐿)|𝑎  
𝐿 → 𝐿, 𝑆 | 𝑆
### 列出终结符、非终结符和开始符号
- 终结符号：a  (  )  ,  
- 非终结符号：L  S  
- 开始符号：S  
### 给出下列句子的语法树
#### (a, a)
![image](https://user-images.githubusercontent.com/49871906/235140002-e32980e8-f0c5-4fec-a2f7-5faf5f69dccb.png)
#### (a, (a, a))
![image](https://user-images.githubusercontent.com/49871906/235140008-019dd654-ef4d-4e8e-994a-b25bffc7ee02.png)
#### (a, ((a, a), (a, a)))
![image](https://user-images.githubusercontent.com/49871906/235140032-59f12973-749e-4f08-a599-442e3aee502b.png)
### 构造 b)中句子的最左推导
#### (a, a)
S=>(L)=>(L,S)=>(S,S)=>(a,S)=>(a,a)
#### (a, (a, a))
S=>(L)=>(L,S)=>(S,S)=>(a,S)=>(a,(L))=>(a,(L,S))=>(a,(S,S))=>(a,(a,S))=>(a,(a,a))
#### (a, ((a, a), (a, a)))
S=>(L)=>(L,S)=>(S,S)=>(a,S)=>(a,(L))=>(a,(L,S))=>(a,(S,S))=>(a,((L),S))=>(a,((L,S),S))=>(a,((S,S),S))
=>(a,((a,S),S))=>(a,((a,a),S))=>(a,((a,a),(L)))=>(a,((a,a),(L,S)))=>(a,((a,a),(S,S)))=>(a,((a,a),(a,S)))
=>(a,((a,a),(a,a)))
### 构造 b)中句子的最右推导
#### (a, a)
S=>(L)=>(L,S)=>(L,a)=>(S,a)=>(a,a)
#### (a, (a, a))
S=>(L)=>(L,S)=>(L,(L))=>(L,(L,S))=>(L,(L,a))=>(L,(S,a))=>(L,(a,a))=>(S,(a,a))=>(a,(a,a))
#### (a, ((a, a), (a, a)))
S=>(L)=>(L,S)=>(L,(L))=>(L,(L,S))=>(L,(L,(L)))=>(L,(L,(L,S)))=>(L,(L,(L,a)))=>(L,(L,(S,a)))=>(L,(L,(a,a)))
=>(L,(S,(a,a)))=>(L,((L),(a,a)))=>(L,((L,S),(a,a)))=>(L,((L,a),(a,a)))=>(L,((S,a),(a,a)))=>(L,((a,a),(a,a)))
=>(S,((a,a),(a,a)))=>(a,((a,a),(a,a)))
### 该文法产生的语言是什么？
由a和完全匹配的括号组所组成的字符串，且由逗号相分割
