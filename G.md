# 資料結構

**[簡報](https://docs.google.com/presentation/d/10jPT6YzpmeYkJswN9X6QWLqCfRqZE5v0)**

[TOC]

## 內容
STL (標準模板庫)
pair、tuple (結構、元組)
Vector (動態陣列)
Stack (堆疊)
Queue (佇列)
Deque (雙端佇列)
Linked List (鏈結串列)
bitset
priority_queue (優先佇列)
set (集合)
map (映射)
離散化
Disjoint Sets (DSU並查集)

## bitset

常用函數：
```cpp=
//之後再說
```

**例題：新北_111資訊學科能力競賽_微生物分佈研究**
(網路上我找不到，但題單沒對外公布，所以就不貼了)

思路：
用`bitset<500001> dt[101]`來存每種微生物的分布，因為只有0(不存在)以及1(存在)
以下是tip
```cpp=
bitset<5> bs1;
bitset<5> bs2;
bs1 = 01001;
bs2 = 11001;
bs3 = bs1 | bs2;
bs3 = 11001;
```

AC Code
```cpp=
#pragma GCC optimize("Ofast,fast-math,unroll-loops,no-stack-protector")
#include <bits/stdc++.h>
using namespace std;
#define int long long
#define shixia ios_base::sync_with_stdio(0),cin.tie(0),cout.tie(0)

const int Mxn = 500001;
int x,n;

bitset<Mxn> dt[101];

signed main(){
    shixia;
    cin>>n>>x;
    for(int i=1;i<=n;i++){
        int type,place;
        cin>>type;
        while(type--){
            cin>>place;
            dt[i].set(place);
        }
    }
    while(x--){
        int m,type;
        cin>>m;
        bitset<Mxn> bt; bt.reset();
        while(m--){
            cin>>type;
            bt = bt | dt[type];
        }
        cout<<bt.count()<<"\n";
    }
    return 0;
}
```