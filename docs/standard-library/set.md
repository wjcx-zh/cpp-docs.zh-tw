---
title: "&lt;set&gt; | Microsoft Docs"
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
  - "std.<set>"
  - "std::<set>"
  - "<set>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "set 標頭"
ms.assetid: 43cb1ab2-6383-48cf-8bdc-2b96d7203596
caps.latest.revision: 20
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;set&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義容器範本類別 set 和 multiset，以及其支援的範本。  
  
## 語法  
  
```  
  
#include <set>  
  
```  
  
## 成員  
  
### 運算子  
  
|set 版本|multiset 版本|描述|  
|------------|-----------------|--------|  
|[operator\!\= \(set\)](../Topic/operator!=%20\(set\).md)|[operator\!\= \(multiset\)](../Topic/operator!=%20\(multiset\).md)|測試運算子左邊的 set 或 multiset 物件是否不等於右邊的 set 或 multiset 物件。|  
|[operator\< \(set\)](../Topic/operator%3C%20\(set\).md)|[operator\< \(multiset\)](../Topic/operator%3C%20\(multiset\).md)|測試運算子左邊的 set 或 multiset 物件是否小於右邊的 set 或 multiset 物件。|  
|[operator\<\= \(set\)](../Topic/operator%3C=%20\(set\).md)|[operator\<\= \(multiset\)](../Topic/operator%3C=%20\(multiset\).md)|測試運算子左邊的 set 或 multiset 物件是否小於或等於右邊的 set 或 multiset 物件。|  
|[operator\=\= \(set\)](../Topic/operator==%20\(set\).md)|[operator\=\= \(multiset\)](../Topic/operator==%20\(multiset\).md)|測試運算子左邊的 set 或 multiset 物件是否等於右邊的 set 或 multiset 物件。|  
|[operator\> \(set\)](../Topic/operator%3E%20\(set\).md)|[operator\> \(multiset\)](../Topic/operator%3E%20\(multiset\).md)|測試運算子左邊的 set 或 multiset 物件是否大於右邊的 set 或 multiset 物件。|  
|[operator\>\= \(set\)](../Topic/operator%3E=%20\(set\).md)|[operator\>\= \(multiset\)](../Topic/operator%3E=%20\(multiset\).md)|測試運算子左邊的 set 或 multiset 物件是否大於或等於右邊的 set 或 multiset 物件。|  
  
### 特製化樣板函式  
  
|set 版本|multiset 版本|描述|  
|------------|-----------------|--------|  
|[swap \(set\)](../Topic/swap%20\(set\).md)|[swap \(multiset\)](../Topic/swap%20\(multiset\).md)|交換兩個 set 或 multiset 的項目。|  
  
### 類別  
  
|||  
|-|-|  
|[set 類別](../standard-library/set-class.md)|用於在集合中儲存和擷取資料，集合中包含的項目值是唯一的，而且這些項目值做為索引鍵值，據此自動排序資料。|  
|[multiset 類別](../standard-library/multiset-class.md)|用於在集合中儲存和擷取資料，集合中包含的項目值不須是唯一的，而且這些項目值做為索引鍵值，據此自動排序資料。|  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)