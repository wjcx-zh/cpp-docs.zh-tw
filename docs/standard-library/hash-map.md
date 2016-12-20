---
title: "&lt;hash_map&gt; | Microsoft Docs"
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
  - "std.<hash_map>"
  - "<hash_map>"
  - "std::<hash_map>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "hash_map 標頭"
ms.assetid: 0765708a-a668-42a2-9800-654c857bdcc2
caps.latest.revision: 27
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;hash_map&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  這個標頭已淘汰。 替代文字是 [\<unordered\_map\>](../standard-library/unordered-map.md)。  
  
 定義容器樣板類別 hash\_map 和 hash\_multimap，以及其支援的樣板。  
  
 在 Visual C\+\+ .NET 2003 中，[\<hash\_map\>](#vclrfhash_map_header_file) 和 [\<hash\_set\>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
## 語法  
  
```  
  
#include <hash_map>  
  
```  
  
### 運算子  
  
|Hash\_map 版本|Hash\_multimap 版本|描述|  
|------------------|-----------------------|--------|  
|[operator\!\= \(hash\_map\)](../Topic/operator!=%20\(hash_map\).md)|[operator\!\= \(hash\_multimap\)](../Topic/operator!=%20\(hash_multimap\).md)|測試運算子左邊的 hash\_map 或 hash\_multimap 物件是否不等於右邊的 hash\_map 或 hash\_multimap 物件。|  
|[operator\=\= \(hash\_map\)](http://msdn.microsoft.com/zh-tw/f933cb1c-934d-43f5-aa9e-0b325eb95b85)|[operator\=\= \(hash\_multimap\)](http://msdn.microsoft.com/zh-tw/3fa378b1-0250-4e3f-a130-dc14103fc5e9)|測試運算子左邊的 hash\_map 或 hash\_multimap 物件是否等於右邊的 hash\_map 或 hash\_multimap 物件。|  
  
### 特製化樣板函式  
  
|Hash\_map 版本|Hash\_multimap 版本|描述|  
|------------------|-----------------------|--------|  
|[swap \(hash\_map\)](../Topic/hash_map::swap.md)|[swap \(hash\_multimap\)](../Topic/hash_multimap::swap.md)|交換兩個 hash\_maps 或 hash\_multimaps 的項目。|  
  
### 類別  
  
|||  
|-|-|  
|[hash\_compare 類別](../standard-library/hash-compare-class.md)|描述一個物件，該物件可由任一雜湊相關聯的容器 \(hash\_map、hash\_multimap、hash\_set 或 hash\_multiset\) 當成預設 **Traits** 參數物件使用，以便排序與雜湊處理所包含的項目。|  
|[value\_compare 類別](../standard-library/value-compare-class.md)|提供函式物件，該物件可透過比較 hash\_map 項目的索引鍵值來比較項目，以判斷項目在 hash\_map 中的相對順序。|  
|[hash\_map 類別](../standard-library/hash-map-class.md)|用以儲存及快速擷取集合中的資料，其中每個項目為具有排序鍵 \(其值唯一\) 和相關聯資料值的配對。|  
|[hash\_multimap 類別](../standard-library/hash-multimap-class.md)|用以儲存及快速擷取集合中的資料，其中每個項目為具有排序鍵 \(其值可重複\) 和相關聯資料值的配對。|  
  
## 需求  
 **標頭：**\<hash\_map\>  
  
 **命名空間：**stdext  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)