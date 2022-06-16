## 高階語言

高階語言的核心是「語法理論」

- 利用生成規則(例如:BNF,EBNF等)描述程式的語法·
- 根據生成規則撰寫剖析程式,轉換成語法。
- 對語法進行『解譯』或『編譯』的動作。

![img](https://github.com/stereomp3/sp110b/raw/master/note/picture/C%E5%9F%B7%E8%A1%8C%E8%A8%98%E6%86%B6%E9%AB%94%E5%88%86%E9%85%8D.png)

## 直譯器

- 利用程式解讀該語法樹,並根據節點類型執行對應的動作

## 編譯器

- 撰寫程式將語法樹轉換為組合語言(或目的碼)

## 語意理論

- 高階語言的核心式 " 語法理論 "
  - 利用生成規則 BNF、EBNF描述程式的語法，生成的是一顆樹
  - 對語法樹進行 編譯 或是 解譯(直譯) 的動作，編譯比直譯還要快
  - 詞彙層次: 使用正規表達式(RE: Regular Expression)
  - 語句層次: 使用Context-free Grammar(CFG)

### 範例 7.1快速排序法的C語言程式

```
void quicksort(double a[], int left, int right) {
    int last = left, i;

    if (left >= right) return;

    swap(a,left,Random(left,right));
    for (i = left + 1; i <= right; i++)
        if (a[i] < a[left])
            swap(a,++last,i);
    swap(a,left,last);
    quicksort(a,left,last-1);
    quicksort(a,last+1,right);
}
void swap(double a[], int i, int j) {
    double tmp = a[i];
    a[i] = a[j];
    a[j] = tmp;
}
```

## 範例 7.2快速排序法的Prolog程式

```
quicksort([X|Xs],Ys) :-
  partition(Xs,X,Left,Right),
  quicksort(Left,Ls),
  quicksort(Right,Rs),
  append(Ls,[X|Rs],Ys).
quicksort([],[]).

partition([X|Xs],Y,[X|Ls],Rs) :-
  X <= Y, partition(Xs,Y,Ls,Rs).
partition([X|Xs],Y,Ls,[X|Rs]) :-
  X > Y, partition(Xs,Y,Ls,Rs).
partition([],Y,[],[]).

append([],Ys,Ys).
append([X|Xs],Ys,[X|Zs]) :- append(Xs,Ys,Zs).
```

