---
title: "&lt; 數值 &gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::<numeric>"
  - "std.<numeric>"
  - "<numeric>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "< 數值 > 標頭"
ms.assetid: 6d6ccb94-48cc-479b-b4a9-bd9c78d4896a
caps.latest.revision: 23
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt; 數值 &gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義可執行數值處理演算法的容器樣板函式。  
  
## <a name="syntax"></a>語法  
  
```  
#include <numeric>  
```  
  
## <a name="remarks"></a>備註  
 這些演算法類似標準範本庫 (STL) 演算法，不過是 C++ Standard 程式庫的一部分。 然而，它們與 STL 相容，而且如同 STL 演算法，它們可以在各種資料結構上作業。 其中包括 STL 容器類別 — 比方說， [向量](../standard-library/vector-class.md) 和 [清單](../standard-library/list-class.md), ，以及程式定義資料結構和滿足特定演算法需求的項目陣列。 演算法間接透過迭代器存取和周遊容器的項目，來達成這個一般性層級。 演算法處理迭代器範圍 (通常由其開始或結束位置指定)。 參考的範圍必須是有效的，這表示在範圍內的所有指標必須都是可取值且在每個範圍的序列中，而且最後一個位置必須可透過遞增從第一個位置連接。  
  
 演算法擴充每一個 STL 容器的作業和成員函式所支援的動作，而且能夠同時與不同類型的容器物件互動。  
  
### <a name="functions"></a>函式  
  
|||  
|-|-|  
|[累積](../Topic/%3Cnumeric%3E%20functions.md#accumulate)|透過計算後續部分總和，計算在指定範圍中所有項目的總和 (包括特定初始值)，或計算後續部分結果 (取得方式是使用指定的二進位運算而非總和運算) 的結果。|  
|[adjacent_difference](../Topic/%3Cnumeric%3E%20functions.md#adjacent_difference)|計算在輸入範圍中每個項目及其前置項之間的後續差異並將結果輸出至目的範圍，或計算一般化程序的結果，其中由另一個指定的二進位運算取代差異作業。|  
|[inner_product](../Topic/%3Cnumeric%3E%20functions.md#inner_product)|計算兩個範圍的項目乘積的總和並將它加入至指定的初始值，或計算一般化程序的結果，其中由另一個指定的二進位運算取代總和與乘積運算。|  
|[iota](../Topic/%3Cnumeric%3E%20functions.md#iota)|儲存開始值，從第一個項目開始，並在間隔 `value++` 中每一個項目，以值的後續增量 (`[first, last)`) 填滿。|  
|[partial_sum](../Topic/%3Cnumeric%3E%20functions.md#partial_sum)|計算一系列總和，在輸入範圍中從第一個項目到 *我*個項目，並將每個總和的結果 *我*個元素的目的範圍，或計算一般化程序，其中由另一個取代總和運算的結果指定的二進位運算。|  
  
## <a name="see-also"></a>請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)

