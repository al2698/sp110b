# CPU0

```
CPU0 是一個 32 位元的處理器，包含 R0..R15, IR, MAR, MDR 等暫存器

CPU0 = ALU + 暫存器 + 控制單元

CPU0有16個暫存器

四大指令 :載入儲存(LD,ST..)，運算(ADD,SUB,XOR..)，跳躍(JMP,JGT..)，堆疊(PUSH,POP..)

指令執行三大階段: 提取，解碼，執行
以下指令的執行步驟

*提取階段
動作1、提取指令 ：IR = [PC]
動作2、更新計數器 ：PC = PC + 4

*解碼階段
動作3、解碼 ：控制單元對IR進行解碼後，設定資料流向開關與 ALU 的運算模式

*執行階段
動作4、執行 ：資料流入 ALU，經過運算後，流回指定的暫存器
```

![img](https://github.com/Kenttsai1/sp110b/raw/master/pict/cpu0.png)

## CPU0指令圖

![img](https://github.com/Kenttsai1/sp110b/raw/master/pict/cpu01.png)

## 狀態暫存器

```
CPU0 的狀態暫存器包含 N, Z, C, V 等狀態，以及 I, T 等中斷模式位元。
```

### 參考來源

[CPU0處理器的架構](http://ccckmit.wikidot.com/ocs:cpu0) [老師PPT](https://www.slideshare.net/ccckmit/2-73472886)
