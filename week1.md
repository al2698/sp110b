# gcc

假設我們寫好一個 C 程式，常程式碼儲存在 hello.c 這個檔案中 若要將 C 的原始碼編譯成執行檔，可以執行 gcc 並指定 C 語言的原始碼檔案 GCC 預設會執行編譯與連結，直接產生一個可以執行的程式，輸出至 a.out 這個檔案，完成編譯之後，即可執行這個程式 若要指定輸出的執行檔名稱，可以加上 -o 參數，並指定輸出的檔案名稱：

```
# 編譯 C 程式，指定輸出檔名
gcc -o hello hello.c

# 執行編譯好的程式
./hello
```

# 介紹

GNU Compiler Collection也稱為GCC編譯器，是一套以GPL及LGPL許可證所發行的自由軟體，是GNU計劃的關鍵部分，也是自由的類Unix及蘋果計算機Mac OS X操作系統的標準編譯器。

GCC（特別是其中的C語言編譯器）也常被認為是跨平台編譯器的事實標準。

GCC原名為GNU C語言編譯器（GNU C Compiler），因為它原本只能處理C語言。GCC很快地擴展，變得可處理C++。之後也變得可處理Fortran、Pascal、 Objective-C、Java，以及Ada與其他語言。

GCC包括以下幾種不同的編譯器：

- gcc： C編譯器
- g ++：C ++和Objective-C編譯器
- gfortran： Fortran編譯器
- gcj：Java編譯器
- GNAT：Ada編譯器
- gccgo： Go編譯器 GCC的模塊化設計還允許安裝插件以擴展軟體的功能，例如增加其他編程語言的支持。

GCC的一大功能是可以針對不同平台交叉編譯程序。這意味著，即使開發人員在一個平台上使用GCC，也可以針對另一個目標平台進行編譯。

GCC是在基於Unix的系統上編譯C和C ++程序的最常見選擇之一。如果您正在為Linux開發，那麼GCC是一個不錯的選擇。它也可以用於Windows，不過通常首選其他編譯器，例如Microsoft Visual Studio附帶的編譯器。


