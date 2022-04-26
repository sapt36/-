專題題目：BCD計算機
=====
```
組員姓名：
        葉徽鄅(U10916019)  劉莉庭(U10916001)
        陳冠廷(U10916040)  吳柏毅(U10916033)
        周冠穎(U10716050)  周哲豪(U10716051)
```

##  <1>  摘要
### 全世界第一台電腦就是一台跟教室一樣大的計算機，所以我們要做出一台簡單的計算機。
##  <2>  製作目的
### 用quartusII和CPLD邏輯設計實驗平台實現BCD的加減乘除，將運算結果在7段顯示器上顯示。
##  <3>  方法探討
   * 加法 : 直接用加法器做，乘法也有乘法器
   * 減法 : 因為減法可能會出現負數，得設定成一定是大減小，不管先輸入的是哪一個數字，再畫truth table跟k-map化簡拉電路
   * 乘法 : 直接用乘法器做
   * 除法 : 因為除法可能會出現分數，不只得設定成一定是大除以小，還要無條件捨棄小數點，得畫truth table跟k-map化簡再拉電路
##  <4>  提出方法及步驟
### 輸入的部分就用 ![image](https://github.com/sapt36/Final-project-of-DigitalCircuitExperiment/blob/main/png/%E5%9C%96%E7%89%876.png) ，左邊四格是第一個數字，右邊四格是第二個數字。
### ![image](https://github.com/sapt36/Final-project-of-DigitalCircuitExperiment/blob/main/png/%E5%9C%96%E7%89%872.png) 這四個分別是加減乘除。如(三)裡提到，將計算結果透過七段顯示器![image](https://github.com/sapt36/Final-project-of-DigitalCircuitExperiment/blob/main/png/%E5%9C%96%E7%89%873.png) 去做輸出。
### 因為BCD的加減乘除會用到十位數，所以會用到兩個七段顯示器，得去設定![image](https://github.com/sapt36/Final-project-of-DigitalCircuitExperiment/blob/main/png/%E5%9C%96%E7%89%875.png)
##  <5>  預期成果
### 一台簡單版的計算機。
##  <6>  參考文獻
### |1|  `[CPLD邏輯設計實驗平台使用手冊]`  |  [CPLD邏輯設計實驗平台使用手冊](https://eeclass.utaipei.edu.tw/media/doc/86181)  |
### |2|  `[BCD維基百科]`  |  [BCD維基百科](https://zh.wikipedia.org/wiki/%E4%BA%8C%E9%80%B2%E7%A2%BC%E5%8D%81%E9%80%B2%E6%95%B8)  |
