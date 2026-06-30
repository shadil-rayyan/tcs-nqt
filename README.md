# 🚀 TCS NQT Previous Year Coding Questions Bank

Welcome to the ultimate repository for TCS NQT preparation! Below you will find curated coding questions frequently asked in technical interviews and assessments, complete with multi-language implementations.

👉 **Looking for more  placement resources ?Check out [Rayyan Coding School Placement Portal](https://rayyancodingschool.shadilrayyan2.workers.dev/)!**

## Resource 
- [ArkS0001/TCS-NQT](https://github.com/ArkS0001/TCS-NQT)
- [GeeksforGeeks](https://www.geeksforgeeks.org/competitive-exam-experiences/tcs-nqt-exam-preparation-and-guide/)
- [Takeuforward](https://takeuforward.org/interviews/tcs-nqt-coding-sheet-tcs-coding-questions/)
- [OnlineStudy4U](https://onlinestudy4u.in/category/tcs-pyq/)
- [Arjunpolen/TCS-NQT-PYQ-QUESTIONS](https://github.com/Arjunpolen/TCS-NQT-PYQ-QUESTIONS)
---
## youTube Video 
- [Quant playlist](https://youtube.com/playlist?list=PLqM7alHXFySEgUZPe57fURJrIt6rXZisW&si=ElnBu7i7G9SFm3F6)
- [Verbal playlist](https://youtube.com/playlist?list=PLqM7alHXFySErksMR-z2wxFMTDV-uiDUO&si=B2XNV79ITQWne0Cs)
- [coding playlist](https://youtube.com/playlist?list=PLqM7alHXFySFSlR00usGeOFRpcFUVYkMp&si=7wq73jd3BZjDqzel)
- [Soft Skill](https://youtube.com/playlist?list=PLqM7alHXFySGesV_XZmdp3_TzJIVJOiad&si=WopTPzMT7cnuOeIK)
  
## 📄 Previous Year Question Papers

👉 [Browse all papers](Question-paper/)

## 📌 Coding Questions

### Q1: Sweet Seventeen
Given a maximum of four digits to the base 17 (where 10 -> A, 11 -> B, ..., 16 -> G) as input, compute and output its decimal value.

<!-- <details>
<summary><b>👁️ View Example & Code Solutions</b></summary> -->

**Input:**
```text
23GF

```

**Output:**

```text
10980

```
#### 💻 Solutions

##### C++

```cpp
#include <iostream>
#include <cstring>
using namespace std;
int main(){
    char hex[17];
    long long decimal = 0;
    cin >> hex;
    int len = strlen(hex);
    long long base = 1;
    for(int i = len - 1; i >= 0; i--) {
        if(hex[i] >= '0' && hex[i] <= '9') {
            decimal += (hex[i] - '0') * base;
        } else if(hex[i] >= 'A' && hex[i] <= 'G') {
            decimal += (hex[i] - 'A' + 10) * base;
        } else if(hex[i] >= 'a' && hex[i] <= 'g') {
            decimal += (hex[i] - 'a' + 10) * base;
        }
        base *= 17;
    }
    cout << decimal;
    return 0;
}

```

##### Java

```java
import java.util.*;
class Main {
    public static void main(String[] args) {
        HashMap<Character, Integer> hmap = new HashMap<>();
        hmap.put('A',10); hmap.put('B',11); hmap.put('C',12); hmap.put('D',13); hmap.put('E',14); hmap.put('F',15); hmap.put('G',16);
        hmap.put('a',10); hmap.put('b',11); hmap.put('c',12); hmap.put('d',13); hmap.put('e',14); hmap.put('f',15); hmap.put('g',16);
        Scanner sin = new Scanner(System.in);
        String s = sin.nextLine();
        long num = 0;
        int k = 0;
        for(int i = s.length() - 1; i >= 0; i--) {
            if(Character.isLetter(s.charAt(i))) {
                num = num + hmap.get(s.charAt(i)) * (int)Math.pow(17, k++);
            } else {
                num = num + ((s.charAt(i) - '0') * (int)Math.pow(17, k++));
            }
        }
        System.out.println(num);
    }
}

```

##### Python

```python
num = str(input())
print(int(num, 17))

```

---

### Q2: A Sober Walk

A person starts from the origin (0,0) and moves outward in a spiral turning clockwise (Right, Up, Left, Down) sequence. Each turn increases the traveling distance by 10 units. Find the final coordinate after `n` turns.

**Input:**

```text
3

```

**Output:**

```text
-20 20

```

#### 💻 Solutions

##### C++

```cpp
#include <iostream>
#include <cmath>
using namespace std;
int main() {
    int n; cin >> n;
    char c = 'R';
    int x = 0, y = 0;
    while(n) {
        switch(c) {
            case 'R': x = abs(x) + 10; y = abs(y); c = 'U'; break;
            case 'U': y = y + 20; c = 'L'; break;
            case 'L': x = -(x + 10); c = 'D'; break;
            case 'D': y = -y; c = 'R'; break;
        }
        n--;
    }
    cout << x << " " << y;
}

```

##### Java

```java
import java.util.*;
class Main {
    public static void main (String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        char c = 'R'; int x = 0, y = 0;
        while(n > 0) {
            switch(c) {
                case 'R': x = Math.abs(x) + 10; y = Math.abs(y); c = 'U'; break;
                case 'U': y = y + 20; c = 'L'; break;
                case 'L': x = -(x + 10); c = 'D'; break;
                case 'D': y = -y; c = 'R'; break;
            }
            n--;
        }
        System.out.println(x + " " + y);
    }
}

```

##### Python

```python
n = int(input())
c = 'R'
x, y = 0, 0
for i in range(n):
    if c == 'R': x = abs(x) + 10; y = abs(y); c = 'U'
    elif c == 'U': y = y + 20; c = 'L'
    elif c == 'L': x = -(x + 10); c = 'D'
    elif c == 'D': y = -y; c = 'R'
print(x, y)

```

---

### Q3: Word is the Key

Determine if a given input word matches any of the protected language keywords: `break`, `case`, `continue`, `default`, `defer`, `else`, `for`, `func`, `goto`, `if`, `map`, `range`, `return`, `struct`, `type`, `var`.

**Input #1:** `defer` → **Output:** `defer is a keyword`

**Input #2:** `While` → **Output:** `while is not a keyword`

#### 💻 Solutions

##### C++

```cpp
#include <iostream>
#include <cstring>
using namespace std;
int main(){
    char str[16][10] = {"break", "case", "continue", "default", "defer", "else","for", "func", "goto", "if", "map", "range", "return", "struct", "type", "var"}; 
    char input[20]; int flag = 0; cin >> input; 
    for(int i = 0; i < 16; i++){
        if(strcmp(input, str[i]) == 0) { flag = 1; break; }
    } 
    cout << input << (flag == 1 ? " is a keyword" : " is not a keyword");
    return 0;
}

```

##### Java

```java
import java.util.Scanner;
class Main {
    public static void main(String args[]) {
        String str[] = {"break", "case", "continue", "default", "defer", "else","for", "func", "goto", "if", "map", "range", "return", "struct", "type", "var"};
        int flag = 0; Scanner sc = new Scanner(System.in); String input = sc.nextLine();
        for(int i = 0; i < 16; i++) {
            if(str[i].equals(input)) { flag = 1; break; }
        }
        System.out.println(input + (flag == 1 ? " is a keyword" : " is not a keyword"));
    }
}

```

##### Python

```python
keyword = {"break", "case", "continue", "default", "defer", "else", "for", "func", "goto", "if", "map", "range", "return", "struct", "type", "var"}
input_var = input()
print(f"{input_var} is a keyword" if input_var in keyword else f"{input_var} is not a keyword")

```

---

### Q4: Push Empty Chocolate Packets

Given an array containing integers representing chocolate packet sizes, push all empty packets (`0`) to the absolute end of the array/conveyor belt while preserving the initial non-zero order.

**Input:**

```text
8
4 5 0 1 9 0 5 0

```

**Output:**

```text
4 5 1 9 5 0 0 0

```

#### 💻 Solutions

##### C++

```cpp
#include <iostream>
using namespace std;
int main () {
    int n, j = 0; cin >> n;
    int a[n] = { 0 };
    for (int i = 0; i < n; i++) {
        int val; cin >> val;
        if (val != 0) a[j++] = val;
    }
    for (int i = 0; i < n; i++) cout << a[i] << " ";
}

```

##### Java

```java
import java.util.*;
class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int arr[] = new int[n];
        int count = 0;
        for(int i = 0; i < n; i++) {
            int val = sc.nextInt();
            if(val != 0) arr[count++] = val;
        }
        for(int i = 0; i < n; i++) System.out.print(arr[i] + " ");
    }
}

```

##### Python

```python
n = int(input())
L = [0] * n
j = 0
for i in range(n):
    a = int(input())
    if a != 0:
        L[j] = a
        j += 1
print(*(L))

```

---

### Q5: Toggle Binary Bits

Convert a base-10 decimal number to its functional binary format, complement/toggle all individual bits starting from the Most Significant Bit (MSB), and display the resulting base-10 output.

**Input:** `10` (Binary: `1010`) → **Output:** `5` (Toggled Binary: `0101`)

#### 💻 Solutions

##### C++

```cpp
#include <iostream>
#include <cmath>
using namespace std;
int main () {
    int n; cin >> n;
    int k = (1 << (int)(floor(log2(n)) + 1)) - 1;
    cout << (n ^ k);
}

```

##### Java

```java
import java.util.*;
class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int no = sc.nextInt();
        String bin = Integer.toBinaryString(no);
        bin = bin.replace('1', '2').replace('0', '1').replace('2', '0');
        System.out.println(Integer.parseInt(bin, 2));
    }
}

```

##### Python

```python
import math
n = int(input())
k = (1 << int(math.log2(n)) + 1) - 1
print(n ^ k)

```

---

### Q6 & Q7: Weekend Count (Sundays Tracker)

Calculate the exact frequency of Sundays that fall within a window of `n` total cumulative days, given the initial weekday starting string.

**Input:**

```text
mon
13

```

**Output:**

```text
2

```

#### 💻 Solutions

##### C++

```cpp
#include <iostream>
#include <unordered_map>
using namespace std;
int main() {
    string s; cin >> s;
    int a, ans = 0; cin >> a;
    unordered_map<string, int> m = {{"mon",6}, {"tue",5}, {"wed",4}, {"thu",3}, {"fri",2}, {"sat",1}, {"sun",0}};
    if(a - m[s.substr(0, 3)] >= 1) ans = 1 + (a - m[s.substr(0, 3)]) / 7;
    cout << ans;
}

```

##### Java

```java
import java.util.*;
class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String str = sc.next();
        int n = sc.nextInt();
        String arr[] = {"mon","tue","wed","thu","fri","sat","sun"};
        int i = 0;
        for(i = 0; i < arr.length; i++) if(arr[i].equals(str)) break;
        int res = 0; int rem = 6 - i;
        if (n >= rem + 1) res = 1 + (n - rem - 1) / 7;
        System.out.println(res);
    }
}

```

##### Python

```python
s = input()[:3]
a = int(input())
m = {"mon": 6, "tue": 5, "wed": 4, "thu": 3, "fri": 2, "sat": 1, "sun": 0}
ans = 0
if a - m[s] >= 1:
    ans = 1 + (a - m[s]) // 7
print(ans)

```

---

### Q8: Risk Severity Sorting

Airport security elements contain three explicit ranges of high risk (`0`, `1`, or `2`). Efficiently sort the items in Linear Time $O(N)$ based purely on ascending classification risk parameters.

**Input:**

```text
7
1 0 2 0 1 0 2

```

**Output:**

```text
0 0 0 1 1 2 2

```

#### 💻 Solutions

##### C++

```cpp
#include <iostream>
using namespace std;
int main() {
    int n; cin >> n; int a[n];
    for(int i = 0; i < n; i++) cin >> a[i];
    int l = 0, m = 0, h = n - 1;
    while(m <= h) {
        if(a[m] == 0) swap(a[l++], a[m++]);
        else if(a[m] == 1) m++;
        else swap(a[m], a[h--]);
    }
    for(int i = 0; i < n; i++) cout << a[i] << " ";
}

```

##### Java

```java
import java.util.*;
class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt(); int arr[] = new int[n];
        int c0 = 0, c1 = 0, c2 = 0;
        for(int i = 0; i < n; i++) {
            arr[i] = sc.nextInt();
            if(arr[i] == 0) c0++; else if(arr[i] == 1) c1++; else c2++;
        }
        while(c0-- > 0) System.out.print("0 ");
        while(c1-- > 0) System.out.print("1 ");
        while(c2-- > 0) System.out.print("2 ");
    }
}

```

##### Python

```python
n = int(input())
arr = [int(input()) for _ in range(n)]
print(*(sorted(arr)))

```

---

### Q9: Prior Dominant Elements Count

Count how many array units remain strictly greater than every separate item existing previous to it. Note: The first element always starts with a relative index match condition.

**Input:**

```text
5
7 4 8 2 9

```

**Output:**

```text
3

```

#### 💻 Solutions

##### C++

```cpp
#include <iostream>
#include <climits>
using namespace std;
int main() {
    int n, c = 0, a, m = INT_MIN; cin >> n;
    while(n--) {
        cin >> a;
        if(a > m) { m = a; c++; }
    }
    cout << c;
}

```

##### Java

```java
import java.util.*;
class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int max = Integer.MIN_VALUE, count = 0;
        for(int i = 0; i < n; i++) {
            int val = sc.nextInt();
            if(val > max) { max = val; count++; }
        }
        System.out.println(count);
    }
}

```

##### Python

```python
import sys
n = int(input())
c, m = 0, -sys.maxsize - 1
for _ in range(n):
    a = int(input())
    if a > m:
        m = a
        c += 1
print(c)

```

---

### Q10: Supermarket Digit Multiplication Pricing

Compute the unique pricing schema of an asset structure by parsing integers and evaluating the direct compound multiplication product of all unique component digits.

**Input:** `5244` → **Output:** `160` (Explanation: $5 \times 2 \times 4 \times 4 = 160$)

#### 💻 Solutions

##### C++

```cpp
#include <iostream>
using namespace std;
int main() {
    string s; cin >> s;
    int p = 1;
    for(auto i : s) p *= (i - '0');
    cout << p;
}

```

##### Java

```java
import java.util.*;
class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int res = 1;
        while(n > 0) {
            res = res * (n % 10);
            n = n / 10;
        }
        System.out.println(res);
    }
}

```

##### Python

```python
n = input()
p = 1
for i in n:
    p *= int(i)
print(p)

```

---

## 🚀 Accelerate Your Career Preparation!

👉 **Looking for more  placement resources ?Check out [Rayyan Coding School Placement Portal](https://rayyancodingschool.shadilrayyan2.workers.dev/)!**



