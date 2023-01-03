# 數據結構(讀書心得)
數據結構(讀書心得)

###### tags: `讀書筆記`

[TOC]
# 數據結構
# 目錄

# 什麼是資料結構
+ 資料結構 : 資料 + 定義資料之間的關係(新增/刪除)
    + 資料之間的關係如何改變,
        + 1.改變觀點(將array看成樹)
        + 2.改變實際資料的排序
+ 演算法 : 使用資料的策略
    + 假如沒有資料結構,可以用的演算法就會很少(暴力法,枚舉法)
    + 所以資料結構,就是為了創造更多的使用策略(遍歷/二元搜尋/動態規劃DP)
   
+ ex. 資料 : 5, 8, 7, 6, 3, 9, 12
    + 策略:
        + 資料結構使用:二元樹搜尋樹(Binary Search Tree)
        + 演算法使用:中序遍歷
        + Tree Sort
    + 策略:
        + 資料結構使用:二元樹搜尋樹(Binary Search Tree)
        + 演算法使用:搜尋
        + Binary Search
    + 策略:
        + 資料結構使用:二元樹堆積樹(Binary Heap Tree)
        + 演算法使用:remove
        + Heap Sort


# Big O
+ Big O
    + 目的 : 提供簡化版的演算法分析方法
    + 意義 : 做一件事情的(成本)與(n)的關係
    + N計算的注意事項
        + 1.高次方會蓋掉低次方 (N的5次方 + N的10次方) => N的10次方
        + 2.忽略常數 (N的平方 + 1) => N的平方 (把N想成無限大)
+ 範例
```java=
//1. 1+3N => N, N趨近於無限大,所以把常數省略
for(int i = 0; i<n; i++){
    x++;
}

//2. n平方
for(int i = 0; i<n; i++){
    for(int j = 0; j<n; j++){
        x++;
    }
}

//3. n + n平方 => n平方
for(int i = 0; i<n; i++){
    x++;
}
for(int i = 0; i<n; i++){
    for(int j = 0; j<n; j++){
        x++;
    }
}

//4. N(1)
int a = 5;
int b = 6;
int temp = a;
int a = b;
int b = temp;

//5. logN
int i = 1;
while(i<n){
    i = i * 2;
}

```
+ 排序
    + O(1) 
        +  index查詢
        +  陣列讀取
        +  hash search
    + O(log n) 
        + 這裡的log是以2為底
        + 二分查找
        + 階層數3
        + ![](https://i.imgur.com/9i0rs0n.png)
    + O(n)
        + 線性
        + 陣列查詢
    + O(n * log n)
        + 線性 + 階層數
        + 合併排序(Merge Sort)
        + 快速排序(Quick Sort)
    + O(n平方)
        + 線性 * 線性 
        + 選擇排序法、插入排序法、泡沫排序法
        + 底數越來越大,階層小
        + ![](https://i.imgur.com/bn6lZLM.png)
    + O(2的n次方)
        + 底數小(2),階層越來越大,當N大於4時,時間複雜度會高於O(n平方)
        + 費氏數列
        + ![](https://i.imgur.com/eaUaPsy.png)
    + O(n!)
        + n = 8, ex : 8 * 7 * 6 * 5 * 4 * 3 * 2 * 1
        + 排列組合
        + ![](https://i.imgur.com/Ceyf2V0.png)

  
+ 2.空間複雜度 : 內存空間增長的趨勢

```java=
    //1. O(1) 空間複雜度,xy怎麼變都不會影響到空間分配
   int i = 0;
   int j = 0;
   i++;
   j++;
```
    
```java=
    //2. O(n) 空間複雜度
    int[] newArr = new int[n];
    for(inti = 0 ;i<n ; i++){
        newArr[i] = 1;
    }
```



#  Array VS LinkedList
## Array
+ Search 
    + by value(遍佈查詢), BigO:O(n)
        + ![](https://i.imgur.com/GgEmg1W.png)
    + by index, BigO:O(1)
        + ![](https://i.imgur.com/HIGg28q.png)
+ Insert 
    + Best Big O : O(1)
        + 1.直接塞到最後一個
        + 2.沒有觸發擴容(grow)
        + ![](https://i.imgur.com/E0eRp4o.png)
    + avg Big O : O(n)(所有元素往後面移動) + O(n)(grow) => O(n)
        + 如果插在中間,必須把指定位置後面的所有元素往後面移動,在插入進去 
        + ![](https://i.imgur.com/IOUTN98.png)
        + 如果陣列空間不足,還需要擴容(grow)
        + ![](https://i.imgur.com/Hzs7wsG.png)

+ Delete
    + by value ,BigO:O(n) + O(n) => O(n)
        + 先遍佈查詢,刪除後,要把所有元素往前移動
        + ![](https://i.imgur.com/5W8gjtw.png)
    + by index ,BigO:1 + O(n) => O(n)
        + 先index查詢,刪除後,要把所有元素往前移動
## LinkedList
+ ![](https://i.imgur.com/vdKrw7e.png)
+ Search
    + 遍佈查詢, BigO:O(n)
    + ![](https://i.imgur.com/O8ARUqO.png)
+ Insert
    + 最後面:直接在後面一個元素新增就好,不需要擴容, BigO:O(1)
    + ![](https://i.imgur.com/9n5Irxh.png)
    + 中間:遍佈查詢,然後改個指標, BigO:O(n)(遍佈查詢) + O(1)(插入) => O(n)
+ Delete 
    + 遍佈查詢,然後改個指標, BigO:O(n)(遍佈查詢) + O(1)(刪除) => O(n)
## 總結:
+ 如果你在查詢有辦法知道index,就用Array
+ 如果很常新增,就用LinkedList

# Stack and Queue
## Stack
+ 特徵
    + 1.後進先出(Last In First Out,LIFO) or 先進後出(First In Last Out,FILO) 的有序列表
    + 2.只能在同一端進行新增或刪除或存取,可以變化的一端稱作棧頂(Top),另一端稱作棧底(Bottom)
    + 3.先放入元素在棧底
    + 4.入棧(push) 和 出棧(pop)
    + ![](https://i.imgur.com/GnKNg9U.png)

+ 運用
    + 1.遞迴
    + 2.二元樹的遍歷
    + 3.DFS
    + 4.河內塔
        + ![](https://i.imgur.com/vBn19sK.png)
## Queue
+ 特徵
    + 先進先出(First In First Out, FIFO) 
    + 只允許一端進行新增,在另一端刪除
    + ![](https://i.imgur.com/Wuuryt0.png)
+ 運用
    + kafka

## Priority Queue(优先队列)
+ 1.特徵
    + 優先級的Queue,保證每次取出的值都是陣列的最大或最小
    + 將最大值,放到出口,其他不排序
    + 用在代辦事項,每次都把最重要的事放在最前面
    + 時間複雜度
        + 取出最大或最小的元素,BigO:O(1)
        + peek(查看優先級最高的元素)跟pop(刪除)都需要遍歷,BigO:O(n)
+ 2.如何優化
    + Binary Heap Tree(BHT)
    + 可以讓peek跟pop 變成O(logn)
    + 備註:如果再java裡面,Heap藉助了Hash，所以只需要O(1) ???
+ 3.示意圖
    + ![](https://i.imgur.com/kd5OVlP.png)

# 演算法基底策略
## DFS(Depth-First Search): 
+ 深度優先:衝到底
+ 快速找出合格解
+ 遞迴
## BFS(Breadth-First Search):
+ 寬度優先:平均的走
+ 找出最佳解答,最短路徑
+ 迴圈
+ ![](https://i.imgur.com/kW870xD.png)


# 五大演算法策略
## 暴力法(Brutee Force)
+ 硬幹就對了
    + 選擇排序法
    + 氣泡排序法
    + 線性查詢
## 貪婪法 (Greedy algorithm)
+ 每一步選擇中都採取在當前最佳的選擇，從而希望導致結果是最好或最佳的演算法
    + 貪婪法容易過早做決定，因而沒法達到最佳解
    + 示意圖
        + ![](https://i.imgur.com/KttWYvd.png)
        + ![](https://i.imgur.com/3MbLBKu.png)
## 枚舉法(Enumeration)
+ 找出所有解
    + 枚舉法是利用計算機運算速度快、精確度高的特點，對要解決問題的所有可能情況，一個不漏地進行檢驗，從中找出符合要求的答案，因此枚舉法是通過犧牲時間來換取答案的全面性
        + 列出所有可能性,再根據條件判斷此答案是否合適
+ 特點
        + 得到的結果肯定正確
        + 效率低,因為全部都走過一遍
        + 通常用來求極端值
+ 示意圖:
        + ![](https://i.imgur.com/prIkcgq.png)
+ 參考
        + https://www.easyatm.com.tw/wiki/%E6%9E%9A%E8%88%89%E6%B3%95
## 回朔法(Backtracking)
+ 找出合格解
    + 跟枚舉法很像,只是如果遇到條件不符合,就會回頭
    + 回溯法大部份用來解決廣義的搜索問題，從許多可能的解中找出滿足要求的所有解，回溯法可以應用於以下類型
        + 八皇后問題
        + 排列組合
        + 0-1 背包問題
+ 示意圖:
        + ![](https://i.imgur.com/ZoL3Igz.png)

## 分支界線法(Branch and bound method)
+ 找出最佳解
    + Branch : 挑當下最好的路
    + Bound : 沒有比之前最好的答案就回頭
    + DFS深度優先
+ 示意圖:
    +![](https://i.imgur.com/gZU0tuS.png)
        
## 分治法(Divide And Conquer)
+ 先將問題切成小問題,在各個擊破
    + 快速排序(Quick Sort)
    + 合併排序(Merge Sort)
    + 二元樹
    + ![](https://i.imgur.com/Olf4h2m.png)

## 動態規劃(Dynanic programming) 
+ 好像用在圖 吧 ????
+ ![](https://i.imgur.com/2f1rvK1.png)


#  排序算法
## 排序種類
+ 插入排序
    + 直接插入排序(Insertion Sort)
    + 希爾排序(Shell Sort)
+ 選擇排序
    + 選擇排序(Selection Sort)
    + 堆排序(heap Sort)
+ 交換排序
    + 泡沫排序(Bubble Sort)
    + 快速排序(QuickSort)
+ 合併排序法(Merge)
+ 基數排序(Radix)
+ 二元查找

## 插入排序法(Insertion Sort)
+ 每次將一個待排序的紀錄按value大小,插入到前面已排好的位置上,直到全部記錄插入完成
+ ![](https://i.imgur.com/O21eJjQ.png)
+ Space : O(1)
+ BigO
    + 比對數子大小(n),移動元素(n),若有n個元素,則需要n-1次的處理
    + best BigO : O(n)
        + 已經排序好了,只需要比對n次
    + worst BigO : O(n平方)
        + 順序是反過來,每次都要移動元素
    + avg BigO : O(n平方)
+ 算法穩定性 : 好
+ 優化 : 二元查找
+ ![](https://i.imgur.com/LMCyhfR.png)

## 希爾排序(Shell Sort)
+ 先追求表中部份有序,在逐漸逼近全局排序
+ 先將排序表分割成如L[i,i+d,i+2d,...]個子表,對子表排序,重複動作直到d = 1
+ Space : O(1)
+ BigO 
    + worst BigO :  O(n平方)
        + 當增量序列d = 1的時候就跟插入排序法一樣
    + avg BigO : 無法算出來,但就是比O(n平方)好
+ 算法穩定性 : 不穩定
+ 只能用於arrayList(有序的)
+ ![](https://i.imgur.com/PQo5L7X.png)


## 泡排序法(Bubble Sort)
+ 從後往前(或從前往後),兩兩value相比,順序錯誤就交換,直到序列比較完成
+ Space : O(1)
+ BigO : 
    + 比對數子大小(n),交換(n),若有n個元素,則需要交換n(n-1)/2次
    + best BigO : O(n)
        + 已經排序好了,只需要比對n-1次
    + worst BigO : O(n平方)
        + 順序是反過來,每次都要交換元素
    + avg BigO : O(n平方)
+ 算法穩定性 : 好
+ 優化 : 只要發生一次未交換,算法可以直接結束
+ ![](https://i.imgur.com/tlWq3UC.png)

## 快速排序法(QuickSort)
+ 在待排序中,每次都選一個元素pivot作為基準,通過一趟劃分
    + 1.排序將元素pivot擺放在正確位置
    + 2.比元素pivot小都放左邊,比元素pivot大或等於都放右邊
+ 劃分好的兩邊重複做,直到每一個部分內只有一個元素或空為止
+ Space : 
    + best Space O : O(log 2n)
    + worst Space O : O(n平方)
+ BigO : 
    + best BigO : O(log 2n)
        + 每次選到的pivot都能將序列分得很均勻
    + worst BigO : O(n平方)
        + 原本是有序或逆序,效率最差
+ 算法穩定性 : 不穩定
+ 優化
    + 1.隨機取一個元素當pivot
+ ![](https://i.imgur.com/T4eeD72.png)
+ ![](https://i.imgur.com/6bDOKIP.png)
+ ![](https://i.imgur.com/gzUVBwe.png)

### DualQuickSort
+ QuickSort 的進化版,改用三軸
+ https://blog.csdn.net/Regino/article/details/104862546

## 選擇排序法(Selection Sort)
+ 每一趟在待元素中排序選擇關鍵字最小(或最小)的元素加入有序
+ Space : Space O(n)
+ BigO: O(n的平方)
    + 不管怎樣都要需要n-1趟處理,比對n次
+ 算法穩定性 : 不穩定
+ ![](https://i.imgur.com/EVnlaPS.png)

## 堆排序(heap Sort)
+ 等待後面講

## 合併排序法(MergeSort)
+ 將序列從中間切割再切割...,排序後,在合併
+ 合併 : 把兩個有序的陣列合併成一個
+ ![](https://i.imgur.com/ab4cUyp.png)
+ Space : 
    + avg BigO : O(log 2n)
+ BigO : 
    + avg BigO : O(log 2n)
+ 算法穩定性 : 穩定
+ ![](https://i.imgur.com/KB6oe6H.png)
+ Divide and Conquer : 將一個難以直接解決的大問題,分割成規模較小的問題,在各個解決
 
## timSort jdk 1.8
https://blog.csdn.net/u012512265/article/details/91948879?spm=1001.2101.3001.6650.2&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7Edefault-2.no_search_link&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7Edefault-2.no_search_link&utm_relevant_index=4 
 
# Hash 
## 什麼是hash
+ input : 任意資料 
+ hash function
    + 1.將原始資料轉換成hash value
    + 2.將hash value依照設定,分到不同的outPut族群
+ fix-size output : 
    + 固定長度的output
+ 示意圖
    + ![](https://i.imgur.com/CuyxOTC.png)
## Collision 碰撞
+ 當不同input value產生相同的output value,稱作為碰撞
+ Output Size長度越長,碰撞機率越低,但空間複雜度越大,計算時間也會越大
+ Output Size長度越短,碰撞機率越高,空間複雜度越小,計算時間越短
    + 碰撞發生機率 MD5 > SHA1 > SHA256
    + 計算時間 SHA256 > SHA1 > MD5
## Hash的比對
+ output的value不同,input一定不相等
+ output的value相同,input**很高機率**相等
+ 示意圖
    + ![](https://i.imgur.com/bJYATjP.png)
## 為什麼使用hash
+ 將複雜資料簡單化
+ 將複雜資料可計算化
    + rolling hash ???
+ 高效能檢查兩個input是否相等 
    + 風險很小
    + 縮短比對時間,時間複雜度為O(1) ??????
+ 無法回推input
    + 密碼比對
## hash查詢速度與比較
+ 1.Linear Search
    + 用value的比較
    + 時間複雜度 O(n)
    + 示意圖:
        + ![](https://i.imgur.com/aoVxKfW.png)
+ 2.Binary Search
    + 用value的比較
    + 時間複雜度 O(log n),n代表階層數目
    + 先決條件:只有排序好的陣列可以使用
    + 示意圖:
        + ![](https://i.imgur.com/ZibLk1Q.png)
+ 3.Hash Search 
    + by index的查詢
    + 時間複雜度 O(1)
    + 先決條件 : 將value利用公式轉換成某一種陣列的index,查詢前先透過hash function 計算出index,就可以直接查詢
    + 示意圖:
        + ![](https://i.imgur.com/NfkvAyI.png)
    + 缺點:
        + 1.浪費儲存空間
        + 2.程式設計比較複雜
        + 3.需要處裡碰撞
+ 4.分塊查找 
## 如何處理Collision
### Direct Access Table
+ 核心 : 直接把Value變成Array的index
+ 缺點 : 
    + 1.value要是正整數,不然不能當作index
    + 2.空間複雜度高
    + EX.如果今天陣列是[1,1000],轉換成Direct Access Table就會變成[1,...1000],大量消耗空間

### Open addressing
+ 發生Collision,往下一個去放
+ 複雜度
    + Space BigO : input的數量
    + Time BigO : O(1)
    + Time worst BigO : input的數量,input與output數量相同,需要擴容
    + 當output小於input時,需要擴容
+ 示意圖
    + ![](https://i.imgur.com/W5K7n4y.png)


### Chaining
+ 核心 : output的資料結構改成ArrayList + LinkedList
+ 示意圖 : 
    + ![](https://i.imgur.com/HX3iPm0.png)
+ 時間複雜度
    + Insert
        + 利用hash function找到index,再LinkedList新增
        +  O(1) +  O(1) =>  O(1)
    + Search
        + 利用hash function找到index,再LinkedList查詢
    + Delete
        + avg BigO : O(1 + input/output) 
        + worst BigO : input的數量,hash function寫得太爛,全部都被分配到同一個LinkedList
+ 時間複雜度優化 : ArrayList + AVL Tree or R-B Tree
    + Search/Delete
        + worst BigO : log(n)
+ 運用
    + jdk7 : ArrayList + LinkedList
    + 補充:如果惡意程序知道我們用的是Hash算法，則在純鍊表情況下，它能夠發送大量請求導致哈希碰撞，然後不停訪問這些key導致HashMap忙於進行線性查找，最終陷入癱瘓
    + jdk8 : ArrayList + (LinkedList or R-B Tree),當LinkedList size大於8時,自動轉為R-B Tree
    + 補充:只有HashMap，LinkedHashMap和ConcurrentHashMap
    + ![](https://i.imgur.com/G8mIlob.png)
    + HashTable沒有,所以除了synchronized之外,他的數據結構也不好
    + ![](https://i.imgur.com/WpoCkVa.png)
    + 參考文獻
        + https://kknews.cc/zh-tw/code/oegy9qp.html
        + https://www.cxybb.com/article/qq_28033239/98204664
        
# Tree基本介紹
+ ![](https://i.imgur.com/gRJLyb4.png)
## 定義:
+ 不包含迴路
+ 兩個節點(node),只有一條路徑
+ 一顆數如果有N個節點,就會有N-1條路徑

## 二元樹的數據結構
### arrayList轉二元樹
+ 陣列0當作根節點
+ arrayList順序要與完全二元樹對應,不然無法找到各自的相對位置
+ 相對位置計算
    + left node:(i+1) - 1
    + right node:(i+1) * 2
    + Parent Node : (i-1)/2 
+ 高度計算
    + Level: log(i+1)
+ 構造
```java=
    private static class Node{
        public int val;  //
        public boolean isEmpty;  //數據是否為空
    }
```
+ 示意圖
    + ![](https://i.imgur.com/mXfgQUt.png)

+ 只適合完全二元樹,不然很浪費空間,所以不常用
    + ![](https://i.imgur.com/70F6FoA.png)

### linkList轉二元樹
+ ![](https://i.imgur.com/e6FeGKa.png)
+ 構造
```java=
    private static class Node{
        public int val;  //
        public Node liftChild;  //左子節點
        public Node rightChild; //右子節點
    }
```

## 二元樹的遍歷(Traversal)
+ Pre-order(前序遍歷)
    + 立刻印
    + ![](https://i.imgur.com/hod2Ylc.png)
+ In-order(中序遍歷)
    + 左邊回來後印
    + ![](https://i.imgur.com/MEKAGrT.png)
+ Post-order(後序遍歷)
    + 右邊回來後印
    + ![](https://i.imgur.com/L6P5pqV.png)


# Binary Search Tree(BST)
## 特徵
+ 1.所有節點都不相同
+ 2.左小右大(左子樹節點都要小於根節點,右子樹節點都要大於根節點)
## 實作
+ 1.查詢
    + ![](https://i.imgur.com/dOFhlz5.png)
+ 2.新增
    + ![](https://i.imgur.com/SETedOG.png)
+ 3.刪除
    + 1.下面兩邊都是null,直接刪除
        + ![](https://i.imgur.com/LOSaUEB.png)
    + 2.左邊是null,右邊有值 or 右邊是null,左邊有值
        + ![](https://i.imgur.com/ufPUwIZ.png)
    + 3.兩邊都有值
        + 1.找出右節點下方最小值(find right min) or 左節點下方最大值
        + 2.交換(swap values)
        + 3.刪除原本要刪除的節點(delete targe in right-tree)
        + ![](https://i.imgur.com/7d3Xn5c.png)
## Binary Search Tree的時間複雜度
+ 1.search/insert/delete 都一樣
+ 2.best BigO : log(n), 平衡的狀態下
+ 3.worst BigO : n, 樹一路歪斜,
    + 雖然都是n平方,但效率比練表差
        + 1.整理成樹 
        + 2.每次都還要比對另外一邊 
+ 4.結論:BST要在平衡的狀態下,才會好用 
## Tree Sort
+ 1.用BST當作底層的搜尋模式,不過可以有重複的節點
+ 2.DFS left + 使用中序遍歷(in-order) + delete
+ 3.時間複雜度
    + best Big O: n(原始資料的個數) * log(n) + n(使用中序遍歷) = > n * log(n)
    + worst Big O : n(原始資料的個數) * n(階層數) + n(使用中序遍歷) = > n * n


# Binary Heap Tree(BHT)
## 特徵
+ 1.完整的二元樹(少的部分補上空節點),節點完全靠左
+ 2.MaxHeap:上大下小   or   MinHeap:上小下大
+ 3.示意圖 
    + ![](https://i.imgur.com/W7pZMB9.png)

## 操作
+ 1.建立:
    + 1.用BFS的方式找出最後一個子節點不為null的node
    + 2.判斷幾個節點
        + 2.1.只有一個子節點,子節點比較大就交換
        + 2.2.兩個子節點,找出最大的子節點,比他大就交換
    + ![](https://i.imgur.com/sGPpFkE.png)
+ 2.remove
    + 1.用DFS的方式找出最後一個子節點
    + 2.與最上面的節點交換
    + 3.移除最後一個的節點
    + 4.最上面的node開始向下沉
        + 4.1.有兩個子節點,找最大交換
        + 4.2.只有一個子節點,比他大就交換
    + ![](https://i.imgur.com/gSc4PwQ.png)
+ 3.add
    + 1.加到最後一個元素
    + 2.往上移
## Heap Sort
+ 先建立一個Binary Heap Tree,然後一直remove
+ MaxHeap,可以把最大的node取出放到陣列,變成由大到小
+ MinHeap,可以把最小的node取出放到陣列,變成由小到大
## Binary Heap Tree的時間複雜度
+ BigO : n(build heap) + n(n個node) * log(n)(remove) => n * log(n)
+ 因為他是完整的二元樹,所以不會有最差的複雜度,永遠都是n * log(n)

# AVL Tree(Self-Balance)
## 為什麼需要AVL Tree
+ 1.BST嚴重歪斜,看起來像LinkList
+ 2.查詢速度到n平方,甚至比LinkList慢
+ ![](https://i.imgur.com/xyeV8bf.png)
+ 所以需要將樹平衡
    + 1.AVL樹
    + 2.紅黑數
    + 3.替罪羊樹
    + 4.treap
    + 5.伸展樹
## 特徵
+ 1.會自我平衡的二元搜尋樹(BST),保證查詢效率高
+ 2.任何節點的兩顆子樹的高度差不大於1的二叉樹
+ 3.哪一個是平衡二叉樹
+ ![](https://i.imgur.com/Rdo064F.png)
## 旋轉
+ 1.LL(左邊偏左):右旋轉(Right Rotate)
    + ![](https://i.imgur.com/yAq5Loq.png)
    + ![](https://i.imgur.com/vHtFqsn.png)
+ 2.RR(右邊偏右):左旋轉(Left Rotate)
    + ![](https://i.imgur.com/sTH4IBJ.png)
+ 3.RL(右邊偏左):先右再左(Right-Left Rotate)
+ 4.LR(左邊偏右):先左再右(Left-Right Rotate)
    + ![](https://i.imgur.com/LkQZw4W.png)
    + NG
    + ![](https://i.imgur.com/KVAnr3C.png)


+ 詳細步驟
    + 1.複製一個根節點
    + 2.新的根節點的左節點指向原本根節點
    + 3.新的根節點的左節點指向原本根節點的左節點
    + 4.原本根結點換成左節點
    + 5.原本根結點指向改成原本左節點的左節點
    + ![](https://i.imgur.com/9PcriSq.png)

# Red—Black Tree (紅黑樹)
## 為什麼需要Red—Black Tree
+ AVL Tree(1962) 跟 RB Tree(1972) 插入/刪除/查詢 時間複雜度都一樣,那為什麼還要RB Tree

+ AVL Tree : 插入/刪除,左右子樹高度差1就要平衡(平率太高)
    + 插入操作導致不平衡,則需要計算平衡因子(時間複雜度高)
+ Red—Black Tree : 插入/刪除啟動平衡難度比較高(彈性較大),不需要平繁調整樹的型態,就算調整,通常在常數級時間內完成

+ AVL Tree : 如果以查找為主,很少插入/刪除
+ Red—Black Tree : 適用於頻繁插入/刪除

## 特徵
+ 節點定義:
```java=
    public static class RBNode {
        public int val; //
        public RBNode parent; //父節點
        public RBNode liftChild;  //左子節點
        public RBNode rightChild; //右子節點
        public int color; //節點顏色, 0/1表示紅黑
    }
```

+ 紅黑樹是BST的延伸,所以左子節點 < 根結點 < 右子樹節點
+ 紅點的目的 : 觸發平衡機制
+ 五大規則
    + 節點 : Red or Black
    + 根結點 : Black
    + 外部節點(空節點), : Black
    + 兩個紅節點不可相連,如果相連就會觸發平衡機制
    + 任一節點至外部節點:經過相同數量的黑節點
    + ![](https://i.imgur.com/vbtTiYS.png)
+ 性質
    + 最長路徑 <= 最短路徑 * 2
    + ![](https://i.imgur.com/U60VRlP.png)
 
+ 口訣:
    + 左根右,根葉黑,不紅紅,黑路同(還有雙壓)

## 新增
+ 先查詢要插入的位置(同BST)
+ 新結點全部都為紅色
    + 因為黑路同(任一節點至空節點會經過相同數量的黑節點)
+ 插入新結點後,如果破壞紅黑樹特性,就開始觸發平衡機制
    + 根葉黑
    + 不紅紅
+ 如何調整節點顏色,看新節點叔叔的顏色
    + ![](https://i.imgur.com/QCbtVul.png)
    + 如果叔叔為黑色 : 旋轉 + 換色
        + LL : 右旋轉,父爺換色
        + RR : 左旋轉,父爺換色
    + ![](https://i.imgur.com/gOkHyft.png)
        + LR : 先左再右旋轉,兒爺換色
        + RL : 先右再左旋轉,兒爺換色
    + ![](https://i.imgur.com/wXBZVC4.png)
    + 如果叔叔為紅色 : 換顏色 + 再判斷一次
        + 叔父跟爺換顏色,爺節點視為新節點
    + 範例1
    + ![](https://i.imgur.com/EtejZFh.png)
    + 範例2
    + ![](https://i.imgur.com/OOqAHwJ.png)
    + ![](https://i.imgur.com/1nmkVg8.png)
    + ![](https://i.imgur.com/3JprlBL.png)

## 新增範例(完整)
+ ![](https://i.imgur.com/5CmxbKq.png)
+ ![](https://i.imgur.com/dLYLeVh.png)
+ ![](https://i.imgur.com/j2eXUng.png)
+ ![](https://i.imgur.com/G7kc4GY.png)
+ ![](https://i.imgur.com/ZVQvmR5.png)
+ ![](https://i.imgur.com/rvTVc5T.png)
+ ![](https://i.imgur.com/CG7hDOh.png)
+ ![](https://i.imgur.com/3wZow0h.png)
+ ![](https://i.imgur.com/XOKTzzP.png)
+ ![](https://i.imgur.com/aVsG2X9.png)



# 多叉树,多路查找樹(multiway tree)
## 我所知道的的多叉树
+ 2-3 Tree
+ 3-4 Tree
+ B Tree
+ B+ Tree
+ B* Tree
## 為什麼需要多叉树
+ 二元樹缺點:
    + 在構建二元樹時,如果資料量大,需要多次進行I/O操作(資料量大的資料都是存在DB或文件)??,效率影響
    + 節點太多,會造成二元樹的高度太高,會降低操作速度
    
## 多叉树特色
+ 在二元樹中,每個節點,只有一個val,並搭配上兩個子節點,但多叉樹可以多個節點跟多個子節點
+ 多叉樹通過重新組織節點,減少樹的高度,並減少I/O讀寫次數來提升效率



## 2-3 Tree 跟 2-3-4 Tree 
+ 2-3 Tree是由以上兩點構造出來的樹
+ 2-3 Tree所有子節點都在同一層(只要B Tree都要滿足這條件)
+ 有兩個子節點的節點叫做二節點,二節點的節點只有兩種情況
    + 1.沒有子節點
    + 2.兩個以上節點
+ 有三個子節點的節點叫做三節點,一樣只有兩種情況
    + 1.沒有子節點
    + 2.兩個以上節點
+ 2-3 Tree 跟 2-3-4 Tree 跟 二元樹的比較
    + ![](https://i.imgur.com/2FyhJg4.png)

## 如何保證B樹的查找效率
+ 1.若每個節點內的val太少,要查更多層節點,效率低
    + 策略:m叉查找樹中,規定除了根結點以外,
        + 1.任何節點至少都要有[m/2]分岔點
        + 2.任何節點至少都要有[m/2] - 1個value
    + ![](https://i.imgur.com/iWKS3Mi.png)
+ 2.如果不夠平衡,樹還是會很高
    + 策略:m叉查找樹中,規定任何節點,所有子樹的高度都要相同
    + ![](https://i.imgur.com/kwmAjFo.png)

## B樹(B-Tree)
### 特色
+ 1.B:Balance
+ 2.2-3 tree 和 2-3-4 tree也是一種B-Tree
+ 3.B樹有一個概念叫：階,通常用m表示，指的是節點的最多子節點個數，比如2-3樹的m是3
+ 4.B樹中最大的m,就稱之為m叉樹
+ 5.如果根結點不是終端節點,至少有兩個子樹
+ 6.除了根結點以外的所有節點,至少有[m/2]以上分岔點跟[m/2] - 1個以上value
+ 7.所有子節點都需要出現在同一層,保證平衡
+ 8.B-Tree的查詢,從根節點開始,對於每個節點做二分查找,如果查不到,就會一值往下找,直到對應的子節點為空
+ 9.所有的節點,都存放數據,可以中間就查到value了
+ ![](https://i.imgur.com/ieIzMCG.png)
+ 
### 多叉树的查詢
+ ![](https://i.imgur.com/YhLP5OJ.png)

### 多叉树的新增
+ 1.新的元素一定是插入到最底層的終端節點
+ 2.與上層融合
+ 示意圖
+ ![](https://i.imgur.com/2g4HvYi.png)
+ ![](https://i.imgur.com/t5KLU6y.png)
+ ![](https://i.imgur.com/bG40qJD.png)
+ ![](https://i.imgur.com/ACJ7Uts.png)
+ ![](https://i.imgur.com/pmdziY3.png)


## B+樹
### 特色
+ 1.每個子節點對應到一顆子樹
+ 2.所有葉子節點的val都是按照順序排列
+ 3.葉子節點會按照順序相連
+ 4.所有分支節點的val,需要對應到葉子節點中關鍵字的最大值 or 最小值
+ 5.除了葉子節點以外,其他都是用來當作索引,用來對應最底層子節點的關鍵字,不會存資料
+ 6.無論查找是否成功,最終都會走到最下面一層
+ ![](https://i.imgur.com/Hm9cjmf.png)

### 查詢
+ ![](https://i.imgur.com/Sfi5mIU.png)

## 淺談mySQL的B+樹的數據結構
+ mysql 一層是16KB
    + ![](https://i.imgur.com/wiiq6S3.png)

+ 單一索引
    + mysql 一個節點的大小約為16KB,指針默認為6B,id 欄位為bigint為8B,所以一層可以裝16KB/14B = 1142
    + 示意圖 
+ ![](https://i.imgur.com/kyk4Rp2.png)

+ 複合索引
    + 示意圖
    + ![](https://i.imgur.com/bvNMRtZ.png)



### 稠密索引 與 稀疏索引???
https://zhuanlan.zhihu.com/p/261130303
https://zhuanlan.zhihu.com/p/67832788

https://www.jianshu.com/p/a7a2bddfa5ac


     
# 圖 ??
## 為什麼要有圖
+ 1.線性:一對一
+ 2.樹:根結點跟葉子節點,一對多
+ 3.圖:當我們需要多對多,就需要用到圖
 
## 圖的基本介紹
+ 1.兩個節點相連叫做邊
+ 2.節點的邊可以具有零個或多個邊
+ 
## 圖的常用概念
+ 1.頂點(vertex)
+ 2.邊
+ 3.路徑
+ 4.無向圖
+ 5.有向圖
+ 6.帶權圖

## 圖的表示方式
+ 1.鄰接矩陣
+ 2.鄰接表
+ 3.十字連結串列

 
# Redis底層資料結構 ??
+ Hash
+ 跳錶
+ 壓縮列表
+ https://www.gushiciku.cn/pl/gfcA/zh-tw
+ https://www.itread01.com/content/1565056924.html
+ 壓縮列表
+ ![](https://i.imgur.com/jX9306T.png)

# 參考文獻

+ 圖解程式教學 Sam Tsai
https://www.youtube.com/channel/UCZ0PZi7oCPH_eUqBpNbBy0Q

+ 研道难(王道考研)
https://www.youtube.com/watch?v=L-3iJOLk3EM&list=PLl-9hEcChubjZRzIoSdACioC2Fsx-JBup&ab_channel=%E7%A0%94%E9%81%93%E9%9A%BE

+ 无狸夹子
https://www.youtube.com/watch?v=FOGgnsOc7Lk&list=PLo4c6wftqfhBaJoOzQJU4GsLeyIuZ6-PX&index=6&ab_channel=%E6%97%A0%E7%8B%B8%E5%A4%B9%E5%AD%90

+ 图灵学院
https://www.youtube.com/channel/UC1eE3JP46onlndR-jETJxXg/videos

+ 图灵星球
https://www.youtube.com/watch?v=hkwi2rQlPak&list=PLV5qT67glKSGFkKRDyuMfwcL-hwXOc4q_&ab_channel=%E5%9B%BE%E7%81%B5%E6%98%9F%E7%90%83TuringPlanet

+ 尚硅谷IT培训学校
https://www.youtube.com/watch?v=BVtO_Oi3VMc&list=PLmOn9nNkQxJFvyhDYx0ya4F75uTtUHA_f&ab_channel=%E5%B0%9A%E7%A1%85%E8%B0%B7IT%E5%9F%B9%E8%AE%AD%E5%AD%A6%E6%A0%A1

+ 黑马程序员
https://www.youtube.com/watch?v=UNGi3M_b-oQ&list=PLD3Xyx6ef38wJ_z2pzZepTMdsgGFivlS0&ab_channel=%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98
