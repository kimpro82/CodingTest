## BAEKJOON Online Judge

# 문제 > 단계별로 풀어보기 > 3. 반복문 - 1) for문

https://www.acmicpc.net/step/3

(2021.05.25) - `C++`  
(2022.01.31) - `Bash`  
(2022.03.18) - `Golang`  


### **List**

- [2739. 구구단](#2739-구구단)
- [10950. A+B - 3](#10950-ab---3)
- [8393. Sum](#8393-sum)
- [15552. 빠른 A+B](#15552-빠른-ab)
- [2741. N 찍기](#2741-n-찍기)
- [2742. 기찍 N](#2742-기찍-n)
- [11021. A+B - 7](#11021-ab---7)
- [11022. A+B - 8](#11022-ab---8)
- [2438. 별 찍기 - 1](#2438-별-찍기---1)
- [2439. 별 찍기 - 2](#2439-별-찍기---2)
- [10871. X보다 작은 수](#10871-x보다-작은-수)


**※ Note**  

&nbsp;&nbsp; - All the codes of any language for the same problem have basically the same result.  
&nbsp;&nbsp; - `Bash` : skipped the first line; `#!/bin/bash`  
&nbsp;&nbsp; - `C++`* : skipped `main()` function's brace(`{}`) and its outside including two header lines; `#include <iostream>` `using namespace std;`  
&nbsp;&nbsp; - `Golang`* : skipped `main()` function's brace(`{}`) and its outside including two header lines; `package main` `import "fmt"`  
&nbsp;&nbsp; * When any additional header is used, the header block is also noted seperately.


## [2739. 구구단](#list)

> 2

> 2 * 1 = 2  
> 2 * 2 = 4  
> ……  
> 2 * 9 = 18

#### Bash
```bash
read n

for i in {1..9}
do
    echo $n "*" $i "=" $((n * i))
done

# read
```

#### C++
```cpp
int a;
cin >> a;

for (int i = 1; i <= 9; i++)
{
    cout << a << " * " << i << " = " << a * i << endl;
}

return 0;
```

#### Golang
```go
var n int
fmt.Scanln(&n)

for i := 1; i <= 9; i++ {
    fmt.Println(n, "*", i, "=", n * i)
}
```


## [10950. A+B - 3](#list)

> 5  
> 1 1  
> 2 3  
> 3 4  
> 9 8  
> 5 2

> 2 5 7 17 7 (vertically)

#### Bash
```bash
read t

for ((i = 0; i < t; i++))
# for i in {1..$t}          # something wrong
do
    read a b
    echo $((a + b))
done

# read
```

#### C++
```cpp
int t, a, b;
cin >> t;

for (int i = 1; i <= t; i++)
{
    cin >> a >> b;
    cout << a + b << endl;
}

return 0;
```

#### Golang
```go
var t int
fmt.Scanln(&t)

for i := 0; i < t; i++ {
    var a, b int
    fmt.Scanln(&a, &b)

    fmt.Println(a + b)
}
```


## [8393. Sum](#list)

> 10

> 55

#### Bash
```bash
read n
let "sum = 0"

for ((i = 1; i <= n; i++))
do
    let "sum += i"
done

echo $sum

# read
```

#### C++
```cpp
int a;
cin >> a;

int sum = 0;
for (int i = 1; i <= a; i++)
{
    sum += i;
}
cout << sum << endl;

return 0;
```

#### Golang - trial 1
```go
var n int
fmt.Scanln(&n)

var sum int = 0
for i := 1; i <= n; i++ {
    sum += i
}

fmt.Println(sum)
```

#### Golang - trial 2
```go
var n int
fmt.Scanln(&n)

var sum = n * (n + 1) / 2

fmt.Println(sum)
```
> expected to be faster, but not so different from ~~the~~ trial 1  
> (※ my wife claimed "trial 1" doesn't require "the")

## [15552. 빠른 A+B](#list)

> 5  
> 1 1  
> 12 34  
> 5 500  
> 40 60  
> 1000 1000

> 2 46 505 100 2000 (vertically)

#### Bash - trial 1
```bash
read t

for ((i = 0; i < t; i++))
do
    read a b
    echo $((a + b))
done

# read
```
> 시간 초과

#### Bash - trial 2
```bash
# t test cases
read t

# Initialize file.txt that has 0 bytes
cat /dev/null > file.txt                # /dev/null : null device

# Operation
for ((i = 0; i < t; i++))
do
    read a b
    echo $((a + b)) >> file.txt
done

# Standard output through a file
awk '{ print }' ./file.txt

# read
```
> 런타임 에러

#### C++
```cpp
// make cin/cout faster
cin.tie(NULL);
ios_base::sync_with_stdio(false);

int t, a, b;
cin >> t;

for (int i = 1; i <= t; i++)
{
    cin >> a >> b;
    cout << a + b << '\n';          // \n is faster than endl
}

return 0;
```

#### Golang - trial 1
```go
var t int
fmt.Scanln(&t)

for i := 0; i < t; i++ {
    var a, b int
    fmt.Scanln(&a, &b)
    fmt.Println(a + b)
}
```
> Timeout

#### Golang - trial 2
```go
import (
    "fmt"
    "bufio"
    "os"
)
```
```go
var reader = bufio.NewReader(os.Stdin)
var writer = bufio.NewWriter(os.Stdout)
defer writer.Flush()

var t int
fmt.Scanln(&t)

var a, b int
for i := 0; i < t; i++ {
    fmt.Fscan(reader, &a, &b)
    fmt.Fprintln(writer, a + b)
}
```


## [2741. N 찍기](#list)

> 5

> 1 2 3 4 5 (vertically)

#### Bash
```bash
read n

for ((i = 1; i <= n; i++))
do
    echo $i
done

# read
```
> 시간 초과

#### C++
```cpp
// make cin/cout faster
cin.tie(NULL);
ios_base::sync_with_stdio(false);

int a;
cin >> a;

for (int i = 1; i <= a; i++)
{
    cout << i << '\n';              // \n is faster than endl
}

return 0;
```

#### Golang
```go
import (
    "fmt"
    "bufio"
    "os"
)
```
```go
// var reader = bufio.NewReader(os.Stdin)      // do not need
var writer = bufio.NewWriter(os.Stdout)
defer writer.Flush()

var n int
fmt.Scanln(&n)

for i := 1; i <= n; i++ {
    fmt.Fprintln(writer, i)
}
```


## [2742. 기찍 N](#list)

> 5

> 5 4 3 2 1 (vertically)

#### Bash
```bash
read n

for ((i = n; i > 0; i--))
do
    echo $i
done

# read
```
> 시간 초과

#### C++
```cpp
// make cin/cout faster
cin.tie(NULL);
ios_base::sync_with_stdio(false);

int a;
cin >> a;

for (int i = a; i >= 1; i--)
{
    cout << i << '\n';              // \n is faster than endl
}

return 0;
```

#### Golang
```go
import (
    "fmt"
    "bufio"
    "os"
)
```
```go
// var reader = bufio.NewReader(os.Stdin)      // do not need
var writer = bufio.NewWriter(os.Stdout)
defer writer.Flush()

var n int
fmt.Scanln(&n)

for i := n; i > 0; i-- {
    fmt.Fprintln(writer, i)
}
```


## [11021. A+B - 7](#list)

> 5  
> 1 1  
> 2 3  
> 3 4  
> 9 8  
> 5 2  

> Case #1: 2  
> Case #2: 5  
> ……  
> Case #5: 7

#### Bash
```bash
read t

for ((i = 1; i <= t; i++))
do
    read a b
    echo "Case #$i: $((a + b))"
done

# read
```

#### C++
```cpp
int t, a, b;
cin >> t;

for (int i = 1; i <= t; i++)
{
    cin >> a >> b;
    cout << "Case #" << i << ": " << a + b << endl;
}

return 0;
```

#### Golang
```go
var t int
fmt.Scanln(&t)

for i := 1; i <= t; i++ {
    var a, b int
    fmt.Scanln(&a, &b)
    fmt.Printf("Case #%d: %d\n", i, a + b)
}
```


## [11022. A+B - 8](#list)

> 5  
> 1 1  
> 2 3  
> 3 4  
> 9 8  
> 5 2  

> Case #1: 1 + 1 = 2  
> Case #2: 2 + 3 = 5  
> ……  
> Case #5: 5 + 2 = 7

#### Bash
```bash
read t

for ((i = 1; i <= t; i++))
do
    read a b
    echo "Case #$i: $a + $b = $((a + b))"
done

# read
```

#### C++
```cpp
int t, a, b;
cin >> t;

for (int i = 1; i <= t; i++)
{
    cin >> a >> b;
    cout << "Case #" << i << ": " << a << " + " << b << " = " << a + b << endl;
}

return 0;
```

#### Golang
```go
var t int
fmt.Scanln(&t)

for i := 1; i <= t; i++ {
    var a, b int
    fmt.Scanln(&a, &b)
    fmt.Printf("Case #%d: %d + %d = %d\n", i, a, b, a + b)
}
```


## [2438. 별 찍기 - 1](#list)

> 5

> \*  
> \*\*  
> \*\*\*  
> \*\*\*\*  
> \*\*\*\*\*

#### Bash
```bash
read n

for ((i = 1; i <= n; i++))
do
    for ((j = 1; j <= i; j++))
    do
        echo -n '*'
    done

    echo ''
done

# read
```

#### C++
```cpp
int a;
cin >> a;

for (int i = 1; i <= a; i++)
{
    // cout << '*' * i << endl;        // calculate ascii code number(42) * i
    for (int j = 1; j <= i; j++)
    {
        cout << '*' ;
    }
    cout << '\n' ;
}

return 0;
```

#### Golang - trial 1
```go
import (
    "fmt"
    "strings"
)
```
```go
var n int
fmt.Scanln(&n)

var star string = "*"
for i := 1; i <= n; i++ {
    fmt.Println(strings.Repeat(star, i ))
}
```

#### Golang - trial 2
```go
var n int
fmt.Scanln(&n)

var star string = ""
for i := 1; i <= n; i++ {
    star += "*"
    fmt.Println(star)
}
```
> rather slower??


## [2439. 별 찍기 - 2](#list)

> 5

> &nbsp;&nbsp;&nbsp;&nbsp;\*  
> &nbsp;&nbsp;&nbsp;\*\*  
> &nbsp;&nbsp;\*\*\*  
> &nbsp;\*\*\*\*  
> \*\*\*\*\*

#### Bash
```bash
read n

for ((i = 1; i <= n; i++))
do
    for ((j = 0; j < n; j++))
    do
        if [ $j -lt $((n - i)) ]; then
            echo -n ' '
        else
            echo -n '*'
        fi
    done

    echo ''
done

# read
```

#### C++
```cpp
int a;
cin >> a;

for (int i = 1; i <= a; i++)
{
    for (int j = 1; j <= a; j++)
    {
        if (i < a - j + 1)
        {
            cout << ' ' ;
        } else {
            cout << '*' ;
        }
    }
    cout << '\n' ;
}

return 0;
```

#### Golang
```go
import (
    "fmt"
    "strings"
)
```
```go
var n int
fmt.Scanln(&n)

for i := 1; i <= n; i++ {
    fmt.Println(strings.Repeat(" ", n - i) + strings.Repeat("*", i ))   // not , but +
}
```


## [10871. X보다 작은 수](#list)

> 10 5  
> 1 10 4 9 2 3 8 5 7 6

> 1 4 2 3

#### Bash
```bash
read n x
read list

for num in $list
do
    if [ $num -lt $x ]; then
        echo -n "$num "
    fi
done

echo ' '

# read
```

#### C++
```cpp
int n, x;
int arr[10000];                 // .exe file stops when int arr[n], although compilation succeeded
cin >> n >> x;

for (int i = 0; i < n; i++)
{
    cin >> arr[i];
    if (arr[i] < x)
    {
        cout << arr[i] << ' ';
    }
}
cout << '\n';

return 0;
```


#### Golang
```go
var n, x int
fmt.Scanln(&n, &x)

for i := 0; i < n; i++ {
    var num int
    fmt.Scanf("%d", &num)
    if num < x {
        fmt.Printf("%d ", num)
    }
}
// fmt.Println("\b")            // causes wrong?
```