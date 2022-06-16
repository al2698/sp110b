c6 編譯器 是陳鍾誠修改自 c4 的衍生作品。
c4 是 Robert Swierczek 寫的一個小型 C 語言編譯器，全部 527 行的原始碼都在 c4.c 裏 。

c4 編譯完成後，會產生一種《機器碼》放在記憶體內，然後 虛擬機 會立刻執行該機器碼。

在 c4 的基礎上，我們建構了 c6，加入了以下功能：

為程式碼加入中文註解

模組化，將虛擬機 vm 獨立出來

加入目的檔

可以用 -o 儲存目的檔

可以用 -u 印出與 -r 執行目的檔

延伸虛擬機

加入 WRIT 指令做檔案寫入

將字串 ADDR 從 IMM 獨立區分出來 (才能用不同格式列印，也比較好懂)

以下是 c6 編譯器的用法，可以進行《自我編譯》:

$ gcc c6.c -o c6

$ ./c6 test/hello.c
hello, world
exit(0) cycle = 9

$ ./c6 c6.c test/hello.c
hello, world
exit(0) cycle = 9    
exit(0) cycle = 28793
c6 在 Windows / Linux / MAC 中都可以執行，使用的精簡過的 C 語言語法！

int main()映出整個主程式
4: {
5:   printf("hello, world\n");
    1:660098     ENT  0   觀看虛擬機語法(https://github.com/ccc-c/c6/wiki/vm)
    3:6600A8     ADDR 0:6A00A0 區分位置還是常數
    5:6600B8     PSH
    6:6600C0     PRTF
    7:6600C8     ADJ  1
6:   return 0;
    9:6600D8     IMM  0
    B:6600E8     LEV
7: }
LEA : load local address 載入區域變數位址                       a = (int)(bp + *pc++); 
IMM : load immediate 載入立即值                                a = *pc++;
ADDR: load global address 載入位址 （通常是字串常數）             a = *pc++;
JMP : jump               跳躍指令                              pc = (int *)*pc;
JSR : jump to subroutine 跳到副程式                            *--sp = (int)(pc + 1); pc = (int *)*pc;
BZ  : branch if zero     if (a==0) goto m[pc]                 pc = a ? pc + 1 : (int *)*pc;
BNZ : branch if not zero if (a!=0) goto m[pc]                 pc = a ? (int *)*pc : pc + 1;
ENT : enter subroutine   進入副程式                            *--sp = (int)bp; bp = sp; sp = sp - *pc++;
ADJ : stack adjust       調整堆疊                              sp = sp + *pc++;
LEV : leave subroutine   離開副程式                            sp = bp; bp = (int *)*sp++; pc = (int *)*sp++;
LI  : load int           載入整數                              a = *(int *)a;
LC  : load char          載入字元                              a = *(char *)a;
SI  : store int          儲存整數                              *(int *)*sp++ = a;
SC  : store char         儲存字元                              a = *(char *)*sp++ = a;
PSH : push               推入堆疊                              *--sp = a;
參考資料

https://github.com/ccc-c/c6/wiki
