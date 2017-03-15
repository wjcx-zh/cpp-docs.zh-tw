---
title: "2.7.2.6 reduction | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: e7630a15-2978-4dbe-a29b-3a46371a0151
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.7.2.6 reduction
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個子句會降低執行純量變數，會出現在*變數清單*，與運算子 op。  語法`reduction`子句是，如下所示：  
  
```  
  
reduction(  
op  
:  
variable-list  
)  
  
```  
  
 減少通常是以下列格式的其中一個陳述式來指定：  
  
```  
  
        x     =  x     op     expr  
x     binop=  expr  
x     =  expr     op     x            (except for subtraction)  
x++  
++x  
x--  
--x  
```  
  
 其中：  
  
 *x*  
 其中一個控制台中的降低變數`list`。  
  
 *變數清單*  
 純量降低變數的逗號分隔清單。  
  
 *expr*  
 已有未參考的純量型別運算式 *x*。  
  
 `op`  
 不是一個多載的運算子，只保留其中 \+、 \*、\-，&、 ^，&#124;，& &、 或 &#124; &#124;  
  
 `binop`  
 不是一個多載的運算子，只保留其中 \+、 \*、\-，&、 ^，或 &#124;。  
  
 下列是範例`reduction`子句：  
  
```  
#pragma omp parallel for reduction(+: a, y) reduction(||: am)  
for (i=0; i<n; i++) {  
   a += b[i];  
   y = sum(y, c[i]);  
   am = am || b[i] == c[i];  
}  
```  
  
 如範例所示，操作員可能會隱藏在函式呼叫內。  使用者應該要小心中所指定的運算子`reduction`子句符合縮減作業。  
  
 雖然的右運算元之 &#124; &#124;運算子有沒有副作用，在本例中，它們允許的但應該謹慎使用。  在此情況下，可能是平行執行期間保證不會在循序執行迴圈期間發生的副作用。  因為反覆執行的順序是不確定，就會發生這種差異。  
  
 運算子用來決定編譯器用它來降低任何私用變數的初始值，並判斷最終處理的操作員。  明確指定運算子，可讓建構的語彙範圍外的縮減陳述式。  任何數目的`reduction`指示詞，可指定子句，但變數可能會出現在最多一個`reduction`該指示詞的子句。  
  
 私用複本中的每個變數的*變數清單*建立時，一個用於每個執行緒，如同`private`所使用的子句。  根據運算子來初始化私用複本 \(請參閱下表\)。  
  
 在其區域結尾處`reduction`子句所指定，原始物件會更新以反映結合原來的值與每個使用指定運算子的私用副本的最終值的結果。  減少運算子 \(除了的減號\)、 所有關聯，而且編譯器可以自由地利用的最終值的計算。  \(減法降低部分結果會加入至表單的最後一個值\)。  
  
 原始物件的值便不定的第一個執行緒到達包含子句期中維持為降低計算直到完成。  一般情況下，計算何時會完成最後的建構。 不過，如果`reduction`子句適用於一種建構的`nowait`是也套用時，原始物件的值不確定之前都會維持障盾同步處理以確保所有的執行緒已完成執行`reduction`子句。  
  
 下表列出有效的運算子和它們的正式的初始設定值。  實際的初始設定值就會減少變數的資料型別完全相同的。  
  
|運算子|初始化|  
|---------|---------|  
|\+|0|  
|\*|1|  
|\-|0|  
|&|~0|  
|&#124;|0|  
|^|0|  
|&&|1|  
|&#124;&#124;|0|  
  
 若要限制`reduction`子句如下：  
  
-   在變數的型別`reduction`子句必須是有效降低運算子的不同之處在於指標型別和參考型別也不允許出現。  
  
-   變數中所指定`reduction`子句不能 **const**\-限定。  
  
-   變數，都是放在平行區域內私用或中顯示的`reduction`的子句**平行**指示詞不能在指定`reduction`工作共用的指示詞，以便繫結到平行建構函式上的子句。  
  
    ```  
    #pragma omp parallel private(y)  
    { /* ERROR - private variable y cannot be specified  
                 in a reduction clause */  
       #pragma omp for reduction(+: y)  
       for (i=0; i<n; i++)  
          y += b[i];  
    }  
  
    /* ERROR - variable x cannot be specified in both  
               a shared and a reduction clause */  
    #pragma omp parallel for shared(x) reduction(+: x)  
    ```