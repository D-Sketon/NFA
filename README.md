
# 使用 Thompson 构造法为下列正规式构造 NFA，写出每个 NFA 处理符号串“𝑎𝑏𝑎𝑏𝑏𝑎𝑏”过程中的状态转换序列
## (a|b)*
![image](https://user-images.githubusercontent.com/49871906/229751826-c2bbb71f-5657-483d-80a6-e55f53bc646c.png)  
0-1-2-3-6-1-4-5-6-1-2-3-6-1-4-5-6-1-4-5-6-1-2-3-6-1-4-5-6-7  
## (a*|b*)*
![image](https://user-images.githubusercontent.com/49871906/229752101-710f4754-093a-41e9-9f80-a3fe00d350cd.png)  
0-1-2-3-4-5-10-1-6-7-8-9-10-1-2-3-4-5-10-1-6-7-8-7-8-9-10-1-2-3-4-5-10-1-6-7-8-9-10-11  
## ((ϵ |a)b*)*
![image](https://user-images.githubusercontent.com/49871906/229752150-eaa26503-3c31-44d5-8af3-350aa32febd9.png)  
0-1-2-3-6-7-8-9-1-2-3-6-7-8-7-8-9-1-2-3-6-7-8-9-10  
0-1-2-3-6-7-8-9-1-2-3-6-7-8-9-1-4-5-6-7-8-9-1-2-3-6-7-8-9-10  
## (a|b)\*abb(a|b)\*
![image](https://user-images.githubusercontent.com/49871906/229752259-92158c62-565b-45b8-97aa-e2636c3b1b54.png)  
0-1-2-3-6-1-4-5-6-7-8-9-10-11-12-13-16-11-14-15-16-17  
# 利用子集构造法将第一题得到的 NFA 转换为 DFA，同样写出分析符号串“𝑎𝑏𝑎𝑏𝑏𝑎𝑏”过程中的状态转换
## (a|b)*
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

## (a*|b*)*
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
## ((ϵ |a)b*)*
NFA初始状态为状态0，A={0, 1, 2, 4, 5, 6, 7, 9, 10}  
- A被加上标记，对于输入符号a,b,有:  
  - B = Dtrans\[A,a\] = ϵ-closure(move(A,a)) = ϵ-closure({3}) = {1, 2, 3, 4, 5, 6, 7, 9, 10}
  - C = Dtrans\[A,b\] = ϵ-closure(move(A,b)) = ϵ-closure({8}) = {1, 2, 4, 5, 6, 7, 8, 9, 10}
- B被加上标记，对于输入符号a,b,有:
  - B = Dtrans\[B,a\] = ϵ-closure(move(B,a)) = ϵ-closure({4}) = {1, 2, 3, 4, 5, 6, 7, 9, 10}
  - C = Dtrans\[B,b\] = ϵ-closure(move(B,b)) = ϵ-closure({8}) = {1, 2, 4, 5, 6, 7, 8, 9, 10}
- C被加上标记，对于输入符号a,b,有:
  - B = Dtrans\[C,a\] = ϵ-closure(move(C,a)) = ϵ-closure({4}) = {1, 2, 3, 4, 5, 6, 7, 9, 10}
  - C = Dtrans\[C,b\] = ϵ-closure(move(C,b)) = ϵ-closure({8}) = {1, 2, 4, 5, 6, 7, 8, 9, 10}  

|NFA状态|DFA状态|a|b|
|-|-|-|-|
|{0, 1, 2, 4, 5, 6, 7, 9, 10}|A|B|C|
|{1, 2, 3, 4, 5, 6, 7, 9, 10}|B|B|C|
|{1, 2, 4, 5, 6, 7, 8, 9, 10}|C|B|C|
## (a|b)\*abb(a|b)\*
NFA初始状态为状态0，A={0, 1, 2, 4, 7}  
- A被加上标记，对于输入符号a,b,有:  
