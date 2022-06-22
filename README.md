# 專題題目：紅綠燈節奏遊戲
```
組員姓名學號：
        葉徽鄅(U10916019)  劉莉庭(U10916001)
        陳冠廷(U10916040)  吳柏毅(U10916033)
        周冠穎(U10716050)  周哲豪(U10716051)
```
###   <-1>  分工表
* 電路機器操作-->葉徽鄅
* 紅綠燈計分-->周哲豪、周冠穎跟吳柏毅
* Github-->陳冠廷
* 循環閃燈-->劉莉庭

##  <0>  目前進度
- [x] 需求分析
- [x] 數位設計
- [x] 電路設計
- [x] 編譯測試
- [x] 結果測試
- [x] 功能測試
- [x] 最終結果
- [ ] 繳交

##  <1>  摘要
###  ___藉由控制紅黃綠LED燈的閃爍快慢進行節奏測試___，LED燈輪流閃爍
### 若碰到綠燈則會加一分，紅燈減一分，黃燈不加分不減分，
### 每加一分則會加快LED燈的閃爍頻率加深關卡難度，
### 得到最高分10分就會結束遊戲。

##  <2>  製作目的
###    用Quartus_II和CPLD邏輯設計實驗平台實現一個節奏遊戲，將得分在7段顯示器上顯示。

##  <3>  方法探討
###     要節奏遊戲就需要有節奏的東西，像是手機遊戲的音樂遊戲，___玩家要跟著節奏在正確的時間點按下螢幕___。
* 然而只憑這個CPLD邏輯設計實驗平台的左半邊應該是辦不到這麼複雜的設計的，
* 畢竟只能用7段顯示器、紅黃綠燈，蜂鳴器等等東西來輸出。
### 所以葉徽鄅想到，有人做過類似音樂遊戲的節奏遊戲，在正確的時間點按下按鈕即勝利。
### 於是我們想到，可以用紅黃綠燈或7段顯示器輪流閃，來做出題的動作
### 後來還討論到，可以做不同的難度(頻率越來越快)，並且可以計算得分，顯示在七段顯示器上。
### 如此一來，就要用紅黃綠燈來做出題了。

##  <4>  提出方法及步驟
###      ___選一個按鍵當作輸入，按下去後紅黃綠燈會自動有規律地輪流閃爍。
### 而若在綠燈時鬆開輸入的那個按鍵加一分；紅燈時鬆開按鍵扣一分；黃燈時鬆開按鍵則不加分也不扣分___。
* 如果做得出來，可以做不同難度的關卡(燈閃爍的頻率越來越快)。
### 為了方便按下隨時放開，我們選用 ___脈波按鍵(PULSE)___ ![image](https://github.com/sapt36/Final-project-of-DigitalCircuitExperiment/blob/main/png/%E5%9C%961.png) 來做輸入。
### 基本上只會用到一個，也就是左上角PS1按鈕。
### 需要像先前作業中那樣，在電路中加上除顫器和Clock。而要輪流跑的紅黃綠燈輪流閃
### ![image](https://github.com/sapt36/Final-project-of-DigitalCircuitExperiment/blob/main/png/%E5%9C%962.png)
### ，並且設成不同難度，最簡單的可能可以每秒換一個燈，越難頻率越快，最難的可能可以1/8秒就換一個燈。
### 而在紅燈時鬆手扣一分，黃燈時鬆手不加分不扣分，綠燈時鬆手加一分。得分則會顯示在七段顯示器上 
### 在控制時序來讓LED燈輪流閃爍 並以電路電線Block Diagram判斷紅黃綠燈的訊號輸入輸出
![image](https://github.com/sapt36/DigitalCircuitExperiment-FinalProject-/blob/main/PIC/%E5%9C%96%E7%89%871.png)
### 而根據按鍵停留在閃爍的哪一個燈上，則是以VHDL判斷並且去做綠燈加分紅燈扣分黃燈不加不減
![image](https://github.com/sapt36/DigitalCircuitExperiment-FinalProject-/blob/main/PIC/%E5%9C%96%E7%89%872.png)
![image](https://github.com/sapt36/DigitalCircuitExperiment-FinalProject-/blob/main/PIC/%E5%9C%96%E7%89%873.png)
* Point symbol
### (先預設分數為0，輸出分數為4bits。其中燈的訊號停留在001也就是綠燈會進行加分，訊號停留在100也就是紅燈且目前分數大於0分會進行扣分
### [但如果目前分數為0分就不繼續扣分了]，再來遇到黃燈010分數不加不減維持一樣)
![image](https://github.com/sapt36/DigitalCircuitExperiment-FinalProject-/blob/main/PIC/%E5%9C%96%E7%89%874.png)
![image](https://github.com/sapt36/DigitalCircuitExperiment-FinalProject-/blob/main/PIC/%E5%9C%96%E7%89%875.png)
* Sevenvhdl symbol 
### (畫好每一個數字的顯示值，再根據分數4-bits來進行七段顯示器的顯示7-bits)
![image](https://github.com/sapt36/DigitalCircuitExperiment-FinalProject-/blob/main/PIC/%E5%9C%96%E7%89%876.png)
* (完整電路圖)

##  <5>  結果與討論
### 我們成功做出按下去會自動輪流閃爍紅黃綠燈，並累積計算得分的節奏遊戲了。
### 在做這個專題時，一開始要解決的問題就是紅黃綠燈的輪流閃爍，
* 邏輯上來說，我們所有的程式都是以此為基礎的。而我們想到用作業六中的移位暫存器來達到自動化。
### 因為對於要在vhdl裡使用clock這部分是沒有學過，沒有經驗的，所以選擇拉電路。
### 接著是控制”按下按鈕才會自動跑”，這部分相當輕鬆，我們則選用最熟悉的switch作為input。
### 接下來是計分，基本上都是做判斷，用if...else基本上就可以了。
* 這部分就全用vhdl寫，比拉電路簡單許多。
### 寫好程式碼之後，在燒錄的時候遇上了不少問題。第一次燒錄的時候，紅黃綠燈會輪流閃，但是數字是反的。
### 改過來之後，數字正了，但是會亂跳，而不是一個一個加。後來想到，可能是第一題就答錯造成得分為負數，而導致無法正常顯示的。
### 於是又加了一個判斷式，使分數最低不低於0。然而，分數還是會亂跳，不過是有規律的一次加兩分而非一次加一分。
* 我們一直想不到為什麼，詢問助教多次也無果。
### 最終突發奇想，可能是即使有用防彈跳，switch的彈跳情形依舊很嚴重，於是嘗試改用pulse作為我們的輸入，至此終於達到預期結果。
### 這次專題花最多時間的部分是在debug。組員都分散各地，討論相當不方便，且需要燒錄進去之後才能開始推測bug在哪裡。
### 再加上線上上課的關係，有問題要問老師或助教都相當困難，且需要等非常久才能得到回應。
### 而且，做專題的同時有許多期末考正在進行中，更是大大壓縮時間。
### 若能提早開始著手準備專題，相信對於時間上的規畫能更加彈性且游刃有餘。

##  <6>  結果圖示
![image](https://github.com/sapt36/DigitalCircuitExperiment-FinalProject-/blob/main/%E6%96%B0%E5%A2%9E%E8%B3%87%E6%96%99%E5%A4%BE/%E5%9C%96%E7%89%877.jpg)
* 當我們使用按下PLUSE後，紅黃綠LED燈開始輪流閃爍
![image](https://github.com/sapt36/DigitalCircuitExperiment-FinalProject-/blob/main/%E6%96%B0%E5%A2%9E%E8%B3%87%E6%96%99%E5%A4%BE/%E5%9C%96%E7%89%878.jpg)
* 紅燈按下後會扣分
![image](https://github.com/sapt36/DigitalCircuitExperiment-FinalProject-/blob/main/%E6%96%B0%E5%A2%9E%E8%B3%87%E6%96%99%E5%A4%BE/%E5%9C%96%E7%89%879.jpg)
* 綠燈按下後加分，黃燈按下後不加不減

##  <7>  參考文獻:book:
### |1|  `[CPLD邏輯設計實驗平台使用手冊]`  |  [CPLD邏輯設計實驗平台使用手冊](https://eeclass.utaipei.edu.tw/media/doc/86181)  |
### |2|  `[電路防彈跳symbol 與 clock symbol]`  |  [電路防彈跳symbol 與 clock symbol](https://eeclass.utaipei.edu.tw/media/doc/85906)  |
### |3|  `[FLIPFLOP和計數器]`  |  [FLIPFLOP和計數器](https://eeclass.utaipei.edu.tw/media/doc/88524)  |
[回到頂部](#readme)
