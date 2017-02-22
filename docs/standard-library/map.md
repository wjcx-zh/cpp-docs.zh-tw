---
title: "&lt; 對應 &gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::<map>"
  - "std.<map>"
  - "<map>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "map 標頭"
ms.assetid: bbf76680-7362-456e-88fa-ecda93561b6a
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# &lt; 對應 &gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義容器樣板類別對應和多重對應，以及其支援的樣板。  
  
## 語法  
  
```  
  
#include <map>  
  
```  
  
## 成員  
  
### 運算子  
  
|對應版本|多重對應版本|描述|  
|----------|------------|--------|  
|[operator\!\= \(map\)](../Topic/operator!=%20\(map\).md)|[operator\!\= \(multimap\)](../Topic/operator!=%20\(multimap\).md)|測試運算子左邊的對應或多重對應物件是否不等於右邊的對應或多重對應物件。|  
|[operator\< \(map\)](../Topic/operator==%20\(map\).md)|[operator\< \(multimap\)](../Topic/operator==%20\(multimap\).md)|測試運算子左邊的對應或多重對應物件是否小於右邊的對應或多重對應物件。|  
|[operator\<\= \(map\)](../Topic/operator%3C%20\(map\).md)|[operator\<\= \(multimap\)](../Topic/operator%3C%20\(multimap\).md)|測試運算子左邊的對應或多重對應物件是否小於或等於右邊的對應或多重對應物件。|  
|[operator\=\= \(map\)](../Topic/operator%3C=%20\(map\).md)|[operator\=\= \(multimap\)](../Topic/operator%3C=%20\(multimap\).md)|測試運算子左邊的對應或多重對應物件是否等於右邊的對應或多重對應物件。|  
|[operator\> \(map\)](../Topic/operator%3E%20\(map\).md)|[operator\> \(multimap\)](../Topic/operator%3E%20\(multimap\).md)|測試運算子左邊的對應或多重對應物件是否大於右邊的對應或多重對應物件。|  
|[operator\>\= \(map\)](../Topic/operator%3E=%20\(map\).md)|[operator\>\= \(multimap\)](../Topic/operator%3E=%20\(multimap\).md)|測試運算子左邊的對應或多重對應物件是否大於或等於右邊的對應或多重對應物件。|  
  
### 特製化樣板函式  
  
|對應版本|多重對應版本|描述|  
|----------|------------|--------|  
|[swap \(map\)](../Topic/swap%20\(map\).md)|[swap \(multimap\)](../Topic/swap%20\(multimap\).md)|交換兩個對應或多重對應的項目。|  
  
### 類別  
  
|||  
|-|-|  
|[value\_compare 類別](../standard-library/value-compare-class-map.md)|提供函式物件，該物件可透過比較對應項目的索引鍵值來比較項目，以判斷項目在對應中的相對順序。|  
|[map 類別](../standard-library/map-class.md)|用於儲存及擷取集合中的資料，集合中的每個項目都有用來自動排序資料的唯一索引鍵。|  
|[multimap 類別](../standard-library/multimap-class.md)|用於儲存及擷取集合中的資料，集合中的每個項目都有用來自動排序資料的索引鍵，而且這些索引鍵不需要具有唯一的值。|  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)