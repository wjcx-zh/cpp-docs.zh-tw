---
title: "&lt;utility&gt; | Microsoft Docs"
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
  - "<utility>"
  - "utility/std::<utility>"
  - "std.<utility>"
  - "std::<utility>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "utility 標頭"
ms.assetid: c4491103-5da9-47a1-9c2b-ed8bc64b0599
caps.latest.revision: 18
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;utility&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可定義標準範本程式庫 \(STL\) 類型、函式與運算子，並協助建構及管理成對的物件，當需要將兩個物件視為一體時相當實用。  
  
## 語法  
  
```  
  
#include <utility>  
  
```  
  
## 備註  
 Standard C\+\+ 程式庫中很廣泛地運用配對。  做為引數並傳回不同函式的值，以及做為容器的項目類型，例如 [map 類別](../standard-library/map-class.md) 和 [multimap 類別](../standard-library/multimap-class.md) 時，都需要用到配對。  \<map\> 會自動納入 \<utility\> 標頭，以協助管理其索引及成對的「鍵\/值」類型項目。  
  
### 類別  
  
|||  
|-|-|  
|[tuple\_element](../standard-library/tuple-element-class-utility.md)|包裝 `pair` 項目類型的類別。|  
|[tuple\_size](../standard-library/tuple-size-class-utility.md)|類別，其中包裝 `pair` 項目計數。|  
  
### 函式  
  
|||  
|-|-|  
|[forward](../Topic/forward.md)|保留引數的參考類型 \(可能是 `lvalue` 或 `rvalue`\)，避免被完整轉寄遮蔽。|  
|[取得](../Topic/get%20Function%20%3Cutility%3E.md)|函式，其可從 `pair` 物件取得項目。|  
|[make\_pair](../Topic/make_pair.md)|範本協助程式函式，可用以建構 `pair` 類型的物件，而其中的元件類型會以傳遞為參數的資料類型做為基礎。|  
|[移動](../Topic/move.md)|傳回已傳入的引數，做為 `rvalue` 參考。|  
|[交換](../Topic/swap%20\(%3Cutility%3E\).md)|交換兩個 `pair` 物件的項目。|  
  
### 運算子  
  
|||  
|-|-|  
|[operator\!\=](../Topic/operator!=%20\(%3Cutility%3E\).md)|測試成對運算子左側的物件是否不等於右側的物件。|  
|[operator\=\=](../Topic/operator==%20\(%3Cutility%3E\).md)|測試成對運算子左側的物件是否等於右側的物件。|  
|[運算子 \<](../Topic/operator%3C%20\(%3Cutility%3E\).md)|測試成對運算子左側的物件是否小於右側的物件。|  
|[運算子 \<\=](../Topic/operator%3C=%20\(%3Cutility%3E\).md)|測試成對運算子左側的物件是否小於或等於右側的物件。|  
|[運算子 \>](../Topic/operator%3E%20\(%3Cutility%3E\).md)|測試成對運算子左側的物件是否大於右側的物件。|  
|[運算子 \>\=](../Topic/operator%3E=%20\(%3Cutility%3E\).md)|測試成寺運算子左側的物件是否大於或等於右側的物件。|  
  
### 結構  
  
|||  
|-|-|  
|[識別](../standard-library/identity-structure.md)||  
|[pair](../standard-library/pair-structure.md)|類型，其提供可將兩個物件視為單一物件的功能。|  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)