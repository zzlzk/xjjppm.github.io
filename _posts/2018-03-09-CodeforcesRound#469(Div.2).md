---
layout: post
title: Codeforces Round 469 (Div.2)
tags:
- CodeForces
categories:
- OI
mathjax: true
---

$\mathrm{pupil}$ 过了 $\mathrm{A,B}$ 已经知足啦！
![qsq](http://images.cnblogs.com/cnblogs_com/NuclearSubmarines/1013327/o_a.png)

# Codeforces Round #469 (Div. 2)

## A. Left-handers, Right-handers and Ambidexters

### 题目大意

有 $l$ 个 $1$，$r$ 个 $0$，$a$ 个可以为 $0$，也可以为$1$ 的数

问最多有多少个 $0,1$ 配对。

### solution

- 水题。

- 如果 $l=r$ ，答案为 $2*(l+\large\lfloor\frac{a}2\rfloor)$ 

- 如果 $l<r$
	- 如果 $l+a<r$，答案为 $2*(l+a)$
	- 如果 $l+a>r$，答案为 $2*(r+\lfloor\large\frac{a-r+l}{2}\rfloor)$

- $l>r$ 同理。

### code

```cpp
#include<cstdio>
#include<cstring>
#include<algorithm>
using namespace std;
typedef long long ll;

template<typename T>
void input(T &x) {
	x=0; T a=1;
	register char c=getchar();
	for(;c<48||c>57;c=getchar())
		if(c==45) a=-1;
	for(;c>=48&&c<=57;c=getchar())
		x=x*10+c-48;
	x*=a;
	return;
}

int main() {
	int l,r,a;
	input(l),input(r),input(a);
	int ans=0;
	if(l<r) {
		if(a>r-l) a-=r-l,ans=r+a/2;
		else if(a==r-l) ans=r;
		else if(a<r-l) ans=l+a;
	} else if(l==r) ans=r+a/2;
	else if(l>r) {
		if(a>l-r) a-=l-r,ans=l+a/2;
		else if(a==l-r) ans=l;
		else if(a<l-r) ans=r+a;
	}
	printf("%d\n",ans*2);
	return 0;
}
``` 

## B. Intercepted Message

### 题目大意

给你一个长为 $n$ 的序列 $x$，长为 $m$ 的序列 $y$。

问的是什么，$\mathrm{pupil}$ 不是很会描述。

解释一下样例吧。

```
input:
7 6  
2 5 3 1 11 4 4  
7 8 2 4 1 8

output:
3
```

$2+5=7$

$3+1+11=8+2+4+1$

$4+4=8$

emmm，大概就这样。

### solution

- 水题。没有看懂题面按照样例解释做没有 $\mathrm{fst}$ 也是很刺激呢。

- $sumx$ 表示没有配对的 $x$ 序列中元素的和，$sumy$ 同理。

- 考虑维护两个指针 $i,j$，$i$ 表示 $x$ 中配对到了哪一个元素，$j$ 同理。

- 每次贪心的选

- 如果 $sumx<sumy$，那就不停地让 `sumx+=x[++i]`，直到$sumx\geq sumy$

- 如果 $sumx=sumy$，那么 `ans++,sumx=x[++i],sumy=y[++j]`

- 如果 $sumy<sumx$，那就不停地让 `sumy+=x[++j]`，直到$sumy\geq sumx$

### code

```cpp
#include<cstdio>
#include<cstring>
#include<algorithm>
using namespace std;
typedef long long ll;

template<typename T>
void input(T &x) {
	x=0; T a=1;
	register char c=getchar();
	for(;c<48||c>57;c=getchar())
		if(c==45) a=-1;
	for(;c>=48&&c<=57;c=getchar())
		x=x*10+c-48;
	x*=a;
	return;
}

#define MAXN 100010
#define MAXM 100010

int x[MAXN],y[MAXM];

int main() {
	int n,m;
	input(n),input(m);
	for(int i=1;i<=n;i++) input(x[i]);
	for(int j=1;j<=m;j++) input(y[j]);
	int ans=0;
	for(int i=1,j=1,sumx=x[1],sumy=y[1];i<=n&&j<=m;)
		if(sumx<sumy) while(sumx<sumy) sumx+=x[++i];
		else if(sumx==sumy) ans++,sumx=x[++i],sumy=y[++j];
		else while(sumx>sumy) sumy+=y[++j];
	printf("%d\n",ans);
	return 0;
}
```

## C. Zebras
$\mathrm{pupil}$ 真的只会做 $\mathrm{A,B}$ 啊！
## D. A Leapfrog in the Array
$\mathrm{pupil}$ 真的只会做 $\mathrm{A,B}$ 啊！
## E. Data Center Maintenance
$\mathrm{pupil}$ 真的只会做 $\mathrm{A,B}$ 啊！
## F. Curfew
$\mathrm{pupil}$ 真的只会做 $\mathrm{A,B}$ 啊！


> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1ODgwMDA4NV19
-->
