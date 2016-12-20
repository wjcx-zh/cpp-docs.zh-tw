---
title: "&lt;hash_set&gt; | Microsoft Docs"
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
  - "<hash_set>"
  - "std.<hash_set>"
  - "std::<hash_set>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "hash_set 標頭"
ms.assetid: 6b556967-c808-4869-9b4d-f9e030864435
caps.latest.revision: 22
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;hash_set&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  此標頭已淘汰。 替代文字是 [\<unordered\_set\>](../standard-library/unordered-set.md)。  
  
 定義容器樣板類別 hash\_set 和 hash\_multiset，以及其支援的樣板。  
  
## 語法  
  
```  
  
#include <hash_set>  
  
```  
  
## 備註  
 在 Visual C\+\+ .NET 2003 中，[\<hash\_map\>](../standard-library/hash-map.md) 和 [\<hash\_set\>](#vclrfhash_set_header_file) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
### 運算子  
  
|Hash\_set 版本|Hash\_multiset 版本|描述|  
|------------------|-----------------------|--------|  
|[operator\!\= \(hash\_set\)](../Topic/operator!=%20\(hash_set\).md)|[operator\!\= \(hash\_multiset\)](../Topic/operator!=%20\(hash_multiset\).md)|測試運算子左邊的 hash\_set 或 hash\_multiset 物件是否不等於右邊的 hash\_set 或 hash\_multiset 物件。|  
|[operator\=\= \(hash\_set\)](http://msdn.microsoft.com/zh-tw/791b95bd-f917-4716-aea6-add50badbfac)|[operator\=\= \(hash\_multiset\)](http://msdn.microsoft.com/zh-tw/cfa9aa0c-d5f6-403a-9441-35c2a4cee0fb)|測試運算子左邊的 hash\_set 或 hash\_multiset 物件是否等於右邊的 hash\_set 或 hash\_multiset 物件。|  
  
### 特製化樣板函式  
  
|Hash\_set 版本|Hash\_multiset 版本|描述|  
|------------------|-----------------------|--------|  
|[swap \(hash\_set\)](../Topic/swap%20\(hash_set\).md)|[swap \(hash\_multiset\)](../Topic/swap%20\(hash_multiset\).md)|交換兩個 hash\_sets 或 hash\_multisets 的元素。|  
  
### 類別  
  
|||  
|-|-|  
|[hash\_compare 類別](../standard-library/hash-compare-class.md)|描述一個物件，該物件可由任一雜湊相關聯的容器 \(hash\_map、hash\_multimap、hash\_set 或 hash\_multiset\) 當成預設 **Traits** 參數物件使用，以便排序與雜湊處理所包含的元素。|  
|[hash\_set 類別](../standard-library/hash-set-class.md)|用於在集合中儲存和擷取資料，集合中包含的元素值是唯一的，並且會作為索引鍵值。|  
|[hash\_multiset 類別](../standard-library/hash-multiset-class.md)|用於在集合中儲存和擷取資料，集合中包含的元素值是唯一的，並且會作為索引鍵值。|  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)