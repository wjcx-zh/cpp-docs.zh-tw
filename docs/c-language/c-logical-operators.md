---
title: "C 邏輯運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "&& 運算子"
  - "|| 運算子"
  - "邏輯 AND 運算子"
  - "邏輯運算子, C"
  - "邏輯運算子, 運算式循序點"
  - "邏輯 OR 運算子"
  - "運算子 [C], 邏輯的"
  - "最短路徑評估"
ms.assetid: c0a4e766-ad56-4300-bf76-b28dc0e19b43
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# C 邏輯運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

邏輯運算子執行邏輯 AND 和 \(**&&**\) 和邏輯 OR \( `||` \) 運算。  
  
 **語法**  
  
 *邏輯運算式*：  
 *Inclusive\-OR 運算式*  
  
 *logical\-AND\-expression*  **&&**  *inclusive\-OR\-運算式*  
  
 *邏輯 OR 運算式*：  
 *邏輯 AND 運算式*  
  
 *邏輯 OR 運算式*  **&#124;&#124;**  *邏輯 AND 運算式*  
  
 邏輯運算子不執行一般算術轉換。  相反地，它們會評估每個運算元是根據其是否為 0。  邏輯運算的結果為 0 或 1。  結果型別為 `int`。  
  
 C 邏輯運算子如下：  
  
|運算子|描述|  
|---------|--------|  
|**&&**|如果兩個運算元具有非零值，邏輯 AND 運算子會得到值 1。  如果任一個運算元等於 0，則結果為 0。  如果 AND 邏輯作業的第一個運算元等於 0，第二個運算元則不會被評估。|  
|`&#124;&#124;`|邏輯 OR 運算子在其運算元上表現為 inclusive\-OR。  如果兩個運算元都有值 0 ，則結果為 0。  如果任一個運算元具有非零值，則結果為 1。  如果邏輯 OR 運算的第一個運算元具有非零值，第二個運算元則不會被評估。|  
  
 邏輯 AND 和邏輯 OR 的運算元其運算式由左至右評估。  如果第一個運算元的值就足以判斷作業的結果，第二個運算元不會被評估。  這稱為「最少運算評估」。有序列點在第一個運算元之後。  如需詳細資訊，請參閱 [序列連接點](../c-language/c-sequence-points.md)。  
  
## 範例  
 下列範例會說明邏輯運算子：  
  
```  
int w, x, y, z;  
  
if ( x < y && y < z )  
    printf( "x is less than z\n" );  
```  
  
 在此範例中，，如果 `x` 小於 `y` ，且 `y` 小於 `z`，`printf` 函式將被呼叫來列印訊息。  如果 `x` 大於 `y`，第二個運算元 \(`y < z`\) 不會被評估且印出 Nothing 。  請注意這可能會造成問題，第二個運算元可能有為其他原因所依賴的副作用。  
  
```  
printf( "%d" , (x == w || x == y || x == z) );  
```  
  
 在此範例中，如果 `x` 等於 `w`、 `y`或 `z`， `printf` 函式評估的第二個引數為 true 且列印出值 1。  否則，它會評估為 false，而列印出值 0 。  當設為 true 的其中一個條件被評估為 true，評估停止。  
  
## 請參閱  
 [邏輯 AND 運算子：&&](../cpp/logical-and-operator-amp-amp.md)   
 [邏輯 OR 運算子：&#124;&#124;](../cpp/logical-or-operator-pipe-pipe.md)